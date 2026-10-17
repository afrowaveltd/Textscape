# Workloads, watchers and the background worker

**Status:** design draft. No task runner or persistent worker is implemented.

## Core concepts

A **workload** specifies what the user wants to accomplish, not merely which URL to visit. A **watcher** follows a durable condition over time, detects new matching state, and triggers an authorized notification or workflow. A tab is a *view* into work, not the worker itself.

Examples:

- `My News`: fetch selected sources (e.g. Seznam, BBC, Guardian, a satirical source if desired); combine article titles/links, detect new stories, cluster related stories without hiding alternate sources, maintain shown/opened/read states, optionally verify claims or translate.
- `New Release`: watch a GitHub/GitLab project or vendor release feed for *any new stable release*, not just a predetermined version; separately configure pre-releases, tags and updates to existing releases. Baseline already-existing items at watcher creation unless history alerts are requested.
- `Watch Author`: track new public articles by an author across configured sources; use explicit author identity/profile matches rather than assuming identical names identify the same person; flag material edits when previous versions are available.
- `Watch Condition`: alert when official release metadata confirms a GA version, when a document appears, when a CVE fix ships, or when a service recovers.
- `Textbird Workflows`: categorize new mail, check links, prepare drafts, summarize GitHub CI notifications; user-allowed auto-replies only via precise rules and audit.

## Collection strategy

Prefer RSS/Atom, structured public APIs, release metadata and conditional HTTP (`ETag`, `Last-Modified`). Use HTML/DOM extraction next; invoke browser JS or AI only if necessary. Respect limits, service terms, robots-related rules where relevant, backoff and authentication boundaries. Distinguish scraping failure from "no new content". The source can disappear or publish multiple entries during an outage; never silently discard gaps.

## Normalized item model

Suggested fields: item ID, source ID, canonical URL, title, author identity link, first-seen timestamp, published/updated timestamps (with source and certainty), content summary or excerpt, content hash, provenance/source attribution, original media language, user states (discovered/shown/opened/read/archived), analysis references, error/status provenance. A topic cluster is distinct from an individual article, so alternative reporting stays visible.

## State and lifecycle

```text
Configured -> Scheduled -> Fetching -> Normalizing -> Comparing
          -> New/Changed/Unchanged/Unknown -> Optional Processing
          -> Persisted -> Notification Pending -> Delivered/Acknowledged
```

Maintain checkpoints, durable retries, idempotent event IDs, deduplication, transactionality, bounded concurrency and cancel/pause/resume. New alerts should not disappear when a tab is merely opened. Different state semantics for mail unread vs article shown vs article read.

## Optional Background Worker

- A separate `textscape-worker` user process can start after login and prepare data before the browser is launched; explicit optional system-level startup only with suitable credentials/security.
- A single logical scheduler owns each job. UI may launch embedded scheduler only when worker is absent and after ownership negotiation; no double processing.
- Local authenticated IPC via Unix socket / Windows Named Pipe; no plaintext network control port by default.
- Tunable concurrency/resource budgets and priorities; delay expensive analysis while the machine is busy, on battery, or memory-constrained without permanently disabling capabilities.
- Honest progress and complete user-visible task history; ability to stop/pause tasks and terminate worker.
- A worker cannot do work when the machine is powered off. Remote always-on execution is a separate optional future extension, not an implied service.

## Watcher plugins

`SourceConnector` discovers items, `ConditionEvaluator` decides if a watched condition changed, `StateStore` remembers baseline and last-seen IDs, `NotificationService` delivers results. Community packs may compose these without obtaining broader privileges. Only authorized external queries are made, with visible domains/data usage.

## Test conditions

First-run baseline, backfilled releases, altered release notes versus new release, changed author byline, duplicate syndication, network outage and recovery, conflicting scheduler instances, cancellation during persistence, restart mid-job, burst notification grouping, correct unread counts, and no unauthorized transmission to AI providers.
