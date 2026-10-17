# Textscape — Implementation Status

> **INITIAL CONCEPT / EARLY DESIGN DRAFT**  
> **Status date:** 2026-10-17  
> **Canonical repository:** https://github.com/afrowaveltd/Textscape  
> **Current phase:** Stage 0 — repository and architecture baseline  
> **Important:** This document reports implementation facts, not the maturity of ideas.

## Current verified state

- **Repository:** published, public, default branch `main` (verified via connected GitHub).
- **Documentation:** an initial English-language architecture and product specification is present.
- **Application source:** **NOT STARTED**. No production Rust workspace, browser, mail client, worker, UI, or extension runtime has been implemented.
- **Automated project tests / CI:** **NOT CONFIGURED / NOT RUN**. There are no legitimate Textscape green-test totals to report.
- **Release artifacts:** none. No alpha, preview, stable version, or software package exists.
- **Project license:** **Civil-only ethical policy direction ACCEPTED; legal license text NOT FINALIZED.** Public source does not grant rights by itself, and the intended restrictions are not OSI Open Source. See [licensing policy](docs/licensing/AFROWAVE-CIVIL-ONLY-POLICY.md) and [ADR 0002](docs/decisions/0002-afrowave-civil-only-policy.md).
- **Localizations:** localization-first is documented; no localization resources or translations have been implemented.
- **Language direction:** **Rust-first core with versioned C ABI and optional narrow C/C++ native adapters ACCEPTED.** No language-specific application source, FFI implementation or toolchain validation exists yet. See [ADR 0001](docs/decisions/0001-rust-first-native-interop.md).
- **Third-party engine selection:** not finalized; candidates are research subjects, not integrated dependencies. Third-party license compatibility remains unverified.

## Component status

The distinction between *documented concept* and *implemented code* is mandatory.

| Component | Design baseline | Implementation | Validation |
| --- | --- | --- | --- |
| Navigator, tabs, TUI, F12 | Initial draft | Not started | Not run |
| Core implementation languages / native FFI | Rust/C ABI/C++ division accepted in principle | Not started | Not run |
| Afrowave Civil-Only licensing | Policy accepted; operative terms pending legal drafting | No LICENSE adopted | Not applicable |
| Web standards, DOM/CSS/layout | Initial draft | Not started | Not run |
| JavaScript runtime adapter API | Initial draft | Not started | Not run |
| ECMAScript / DOM / WASM conformance | Test strategy documented | Not started | Not run |
| Glass House Data Manager / privacy | Principles and architecture draft | Not started | Not run |
| Textbird mail client | Initial draft | Not started | Not run |
| Workloads, Watchers and background Worker | Initial draft | Not started | Not run |
| Event Bus, scheduler and notifications | Initial draft | Not started | Not run |
| Security Link Inspector | Initial draft | Not started | Not run |
| AI provider / agent / prompt interfaces | Initial draft | Not started | Not run |
| Plugin SDK / community catalog | Initial draft | Not started | Not run |
| FactCheck / evidence lineage / Neutral Rewrite | Initial draft | Not started | Not run |
| Terminal shell / clipboard integration | Initial draft | Not started | Not run |
| Localization / accessibility | Initial draft | Not started | Not run |

## Development rules

1. **This file is the canonical current implementation status.** Changes in PRs touching implementation, CI, or milestones must update this file or explicitly explain why no change is needed.
2. Never label something `PASS`, `DONE`, `GREEN`, `RELEASED`, or `SUPPORTED` unless actual artifacts, executions, and verifiable evidence exist.
3. Every implemented requirement must link to a specification, acceptance test, actual test result, and owning component. See [requirements traceability](docs/planning/REQUIREMENTS-TRACEABILITY.md).
4. Keep proposals, accepted decisions, experimental prototypes and production-ready behavior distinct. See [workflow](docs/planning/DEVELOPMENT-WORKFLOW.md) and [ADR log](docs/decisions/README.md).
5. Shared interface changes are coordinated serially with a single owner. Parallel work is reserved for isolated, demonstrably independent tasks.
6. Textscape's Glass House rules apply to the development process too: no silent external actions, hidden telemetry, invented test outcomes, or unauthorized publication of user data.

## Stage 0 checklist

- [x] Initial repository published publicly on GitHub.
- [x] Initial design/architecture documents collected in English.
- [x] Root implementation status and documentation governance added.
- [x] Approve the Rust-first / C ABI / limited C++ language direction (ADR 0001).
- [x] Approve Afrowave Civil-Only licensing *policy direction* (ADR 0002).
- [ ] Finalize and publish a legally reviewed LICENSE and contribution policy; complete dependency compatibility audit.
- [ ] Ratify first architecture decisions using individual ADRs.
- [ ] Agree on minimal implementation target and supported test platforms.
- [ ] Approve first vertical-slice acceptance criteria and test fixture policy.
- [ ] Establish minimal project source structure and CI after the preceding gates.

## Next recommended action

**Complete legally reviewed Afrowave Civil-Only license text, third-party dependency compatibility and contribution policy; then ratify the minimal Stage 1 vertical slice.** The Rust-first/C-ABI direction is agreed, so establish an executable test harness and minimal Rust workspace only after stage-gate acceptance. Next implement a small end-to-end terminal navigation fixture. See [roadmap](docs/planning/ROADMAP.md) and [open decisions](docs/planning/OPEN-QUESTIONS.md).

## Status update record

| Date | Change | Evidence |
| --- | --- | --- |
| 2026-10-17 | Initial concept documentation and Git repository published | [Repository](https://github.com/afrowaveltd/Textscape) |
| 2026-10-17 | Canonical implementation status, docs index and working process established | Initial documentation commits; no implementation or test execution implied |
| 2026-10-17 | Rust-first C ABI / C++ adapter direction accepted; civil-only ethical policy recorded | [ADR 0001](docs/decisions/0001-rust-first-native-interop.md), [ADR 0002](docs/decisions/0002-afrowave-civil-only-policy.md); no source code or final license |

**Reminder:** These checkboxes describe documentation/repository preparation only. They do not imply a functional browser.