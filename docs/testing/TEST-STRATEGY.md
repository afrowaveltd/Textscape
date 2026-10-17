# Specification-first conformance and quality strategy

**Status:** testing charter; no tests are implemented yet.

## Contract: traceability, not vanity pass percentages

Every spec/requirement entry should map to identifiable automated cases where applicable. Store original requirement reference, suite version, test ID, fixture/input, expected behavior, observed behavior, runtime/backend versions, environment, source provenance and reproducibility. A number of passed tests is **not** equivalent to percentage of the overall language specification covered.

Result taxonomy: `PASS`, `FAIL`, `SKIP` (explicitly unsupported/inapplicable), `NOT_RUN`, `TIMEOUT`, `CRASH`, `HARNESS_ERROR`, optionally `FLAKY` when reproducibly detected. No silent conversions from unsupported to pass, harness error to engine failure, or empty run to 100% compliance. Publish per-feature coverage maps and exact error cases.

## Independent suites

1. **ECMAScript:** Test262 and official runner guidelines; correct realms, strict/sloppy modes, negative tests, async jobs, modules and allowed host hooks. Map ECMA-262 sections to test IDs with explicit known holes.
2. **Web APIs/DOM:** Web Platform Tests, cross-origin rules, storage, events, Fetch, WebSocket as implemented; adapt test harness to TUI where tests depend on pixel-level geometry.
3. **WASM:** WebAssembly spec tests plus realistic app smoke tests (including, on supporting engines, an unmodified Blazor WASM counter).
4. **Adapter/core:** engine lifecycle/GC host bindings, UI-command separation, ABI/IPC contracts, crash isolation and async ordering.
5. **Terminal rendering/UX:** snapshots and semantic assertions for cells, split panels, responsive widths, mouse/focus, pulldown details, progress and clipboard.
6. **Textbird:** IMAP/SMTP MIME interoperability, delivery state, read/unread, loop-safe automated replies, drafts, localization and notifications.
7. **Workloads:** idempotency, first-run baselines, RSS and GitHub release fixtures, author identity, change detection, offline retries, resume, scheduler lease conflicts, background desktop notifications.
8. **Privacy/permissions:** cookie HttpOnly, local storage inspection/deletion, policy filters at network boundaries, agent/tool capabilities, exactly-reviewed diagnostic payloads, redaction and user approval.
9. **AI/fact-check:** evidence attribution, source dependence, actor-swap symmetry, neutral wording, fact-vs-opinion, proof of exact citation lineage, prompt/plugin permissions and injection resistance.

## Public conformance UI

`Tools -> Advanced -> Engine Diagnostics`: Quick Check, Feature Check, Full Conformance, Compare Engines; filters by spec clause and failure; export redacted reproducible report; run related tests from F12. Tests execute in isolated contexts and preferably isolated processes to avoid corrupting normal browser session; enforce time/resource limits. Large suites may be slower on constrained hardware without reduced feature availability.

## Test ownership and sequencing

Before implementation define acceptance cases and intentionally failing tests. Assign a single owner to shared interfaces. Parallel work only for genuinely independent research, fixture generation, component implementation, or external verification. Merge one validated change at a time, run CI, record green state. AI-produced fixes get regression test first, independent review and no direct production deployment.

## Future CI (not yet configured)

Rust format/lints/tests, markdown local links, license/SBOM scanning, platform matrix (Linux, Windows, macOS and architectures as feasible), security fuzzing/sanitizers, deterministic fixtures, integration smoke tests, and reproducible release artifacts. Reports distinguish executed vs planned tests.

## Relevant upstream projects

- https://tc39.es/ecma262/
- https://github.com/tc39/test262
- https://github.com/tc39/test262-harness
- https://web-platform-tests.org/
- https://github.com/WebAssembly/spec
