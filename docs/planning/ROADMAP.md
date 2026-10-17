# Development roadmap — initial sequencing proposal

**Not a release commitment.** Milestones are gates, not dates. Avoid building many untested major subsystems concurrently.

## Stage 0 — repository and decision baseline

This documentation seed, decision log, contribution standards, accepted Rust-first/C-ABI/C++ adapter direction and civil-only licensing policy. Final legal text and third-party dependency compatibility remain open gates. Decide target architectures, security assumptions, feature priorities and ownership.

## Stage 1 — minimal core and test harness

Rust workspace prototype under [ADR 0001](../decisions/0001-rust-first-native-interop.md), structured errors, command/event model, config and localization infrastructure, lightweight TUI tabs/URL bar/status, simple storage, deterministic fixtures, CI. Establish conformance infrastructure before adding a JS engine. Basic page navigation/HTML text rendering and inspectable network progress.

## Stage 2 — browser runtime vertical slice

A single chosen JS adapter + minimal DOM bindings with correct async/GC lifetimes; accessible F12, network inspection, cookie/LocalStorage managers and policies. Exercise Test262 subsets and integration fixtures. Prototype second engine to validate adapter portability. Incremental CSS and terminal layout sophistication; image fallback and small-terminal behavior.

## Stage 3 — durable workloads and background execution

Single scheduler, state store, event bus, worker IPC, RSS/news sample, release watcher (GitHub), tab badges and desktop/BEL notifications. First-run baseline, resume/retries and no double execution. User-viewable Worker Activity and configurable power/resource policies.

## Stage 4 — Textbird

IMAP/SMTP/MIME interoperability, message list, rich/plain composition, rules, notifications and mail data management. AI draft workflow only after capability gateway, durable approvals and audit are proven.

## Stage 5 — community extensibility and optional AI

Versioned plugin/connector/prompt SDK, manifest/permission viewer, local plugin runner, catalogue publishing/review process; initial security link inspector. AI provider adapters, visible input/prompt/tool traces, tested policy enforcement.

## Stage 6 — evidence-based reading

Claim-by-claim fact-check, source-lineage and chronology, language manipulation tests and neutral-rewrite profiles; original/derived side-by-side; user-editable prompts; author watcher and optional change follow-ups. Test quality on difficult cases without implying model omniscience.

## Stage 7 — broader coverage, packaging and release

Web conformance expansion, WASM/Blazor proof on supported engines, isolation/fuzzing, accessibility/localization, headless platforms, community docs, reproducible builds and distribution. Additional GUI only if real demand and architecture permits.

## Gates for every stage

- Exact acceptance behavior documented.
- Runnable tests with trustworthy expected results.
- No new hidden data flows or permission bypass.
- Reproducible build and regression coverage.
- Review/signoff before broadening scope.

This ordering is a starting conversation, not an irreversible schedule. Feature prototypes can inform earlier design decisions, but must be labeled experimental.
