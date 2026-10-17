# Initial Requirements and Acceptance Traceability

> **Draft baseline, 2026-10-17.** These are intended outcomes from product discovery, not implemented functions. **All listed automated tests are NOT_RUN / not yet created.** Test IDs below are placeholders, not existing test files.

Keep this list small enough to maintain, but never discard detailed scenarios and standards mapping. As implementation begins, split requirements into atomic, versioned IDs with exact inputs, expected outputs, source references and observed test results.

| ID | Requirement / intended observable behavior | Specification | Planned proof |
| --- | --- | --- | --- |
| TS-CORE-001 | TUI works without graphical desktop, with tabs, URL/navigation, keyboard and mouse | [TUI/UX](../features/TUI-UX.md) | Terminal fixture, input/navigation tests |
| TS-CORE-002 | Shared app services are UI-independent; closing a workload tab does not stop its job | [System](../architecture/SYSTEM.md) | Close/reopen UI with persistent job |
| TS-JS-001 | JS engine adapter implements a documented versioned host contract without leaking engine-native types | [Browser runtime](../architecture/BROWSER-RUNTIME.md) | Adapter contract test on 2 engines |
| TS-JS-002 | Conformance cases map to precise clauses and have reproducible PASS/FAIL/SKIP results | [Testing](../testing/TEST-STRATEGY.md) | Test262/WPT/WASM pilot, honest coverage |
| TS-DATA-001 | Owner inspects, exports, edits where meaningful, and deletes local cookie/storage items | [Glass House](../security/GLASS-HOUSE.md) | Create/inspect/export/delete/verify |
| TS-DATA-002 | Network, storage and AI data operations have visible provenance, and diagnostic payload exactly matches approved bytes | [Glass House](../security/GLASS-HOUSE.md) | Payload integrity + audit fixture |
| TS-SEC-001 | A web page/agent cannot bypass user privacy rules or gain host shell privileges | [Threat model](../security/THREAT-MODEL.md) | Negative capability and sandbox tests |
| TS-WORK-001 | Workload ingests RSS/public data into deduplicated, persistent, user-defined views | [Workloads](../architecture/WORKLOADS.md) | Feed import + restart fixture |
| TS-WORK-002 | Watcher detects truly new release by stable identity, not assumed version format | [Workloads](../architecture/WORKLOADS.md) | Initial baseline/new release/update fixtures |
| TS-WORK-003 | Optional worker executes with single durable task owner; UI can detach/reconnect | [Workloads](../architecture/WORKLOADS.md) | Restart + lease conflict test |
| TS-NOTIF-001 | Notifications display accurate unread/new counts and optional terminal/OS sound without duplicates | [Mail and notifications](../architecture/MAIL-NOTIFICATIONS.md) | Badge and grouped-notification fixtures |
| TS-MAIL-001 | Email originals are preserved; draft/AI operations are audited and never silently sent | [Mail and notifications](../architecture/MAIL-NOTIFICATIONS.md) | MIME + drafts + permission fixture |
| TS-EXT-001 | Community prompt/plugin declares data inputs and permissions; updates are reviewed | [AI/extensions](../architecture/AI-EXTENSIONS.md) | Install/update/escalation tests |
| TS-AI-001 | Optional agents cannot acquire undeclared tools or leak data without authorization | [AI/extensions](../architecture/AI-EXTENSIONS.md) | Injection + deny/allow matrix |
| TS-FACT-001 | FactCheck reports exact claims, evidence and source-lineage (syndicated copies count as one origin) | [FactCheck](../features/FACTCHECK-LANGUAGE.md) | Multi-source provenance fixture |
| TS-LANG-001 | Rewrite uses strongest accurate evidence-supported wording, preserves actors/acts, passes actor-swap symmetry | [FactCheck](../features/FACTCHECK-LANGUAGE.md) | Anti-euphemism + no-overclaim fixture |
| TS-L10N-001 | User-facing strings are localizable; keyboard-only and no-emoji terminals remain usable | [Localization](../features/LOCALIZATION.md) | Locale/fallback/accessibility tests |

## Evidence rules

- A numbered requirement is not a claim of supported functionality.
- A proposed test ID never means it has been written or run.
- For implemented features, add links to *actual* test file, execution record, commit and test environment.
- A failed case remains failed until rerun after a fix; do not replace observed results with assumptions.
- Keep upstream suite versions/license constraints and exclusions explicit. Conformance results are not a universal compliance percentage.
- Changing requirements or a high-level principle requires review and, where warranted, an ADR.

The canonical current feature state is [IMPLEMENTATION_STATUS.md](../../IMPLEMENTATION_STATUS.md), not this prospective matrix.
