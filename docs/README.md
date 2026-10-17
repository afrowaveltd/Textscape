# Textscape Documentation

> **Initial concept / early design draft.** The documentation describes intended behavior. It is not evidence that the application exists or has passed tests.

## Source-of-truth rules

- [`/IMPLEMENTATION_STATUS.md`](../IMPLEMENTATION_STATUS.md) — **canonical current project status**: what exists, what is tested, and what remains planned.
- [Decision log](decisions/README.md) and accepted ADRs — authoritative for **ratified** architecture decisions. A design sketch or proposed decision is not automatically accepted.
- Feature/architecture documents — intended behavior, subject to decision and acceptance tests.
- [Requirement traceability](planning/REQUIREMENTS-TRACEABILITY.md) — requirement identifiers and planned test evidence.
- Source code, runnable tests and CI reports — evidence of implementation and measured behavior once they exist. Design prose cannot override actual reproducible results.
- Discussions, chat transcripts and example prompts — inputs for proposals, **not** canonical specifications until written and reviewed here.

Resolve contradictions explicitly, with a documented decision; do not quietly redefine accepted requirements or overwrite status.

## Product and architecture

| Document | Purpose |
| --- | --- |
| [Vision](VISION.md) | Mission, principles, intended users |
| [System architecture](architecture/SYSTEM.md) | Modules, dependency and trust boundaries |
| [Rust / C / C++ language architecture](architecture/LANGUAGE-AND-FFI.md) | Language ownership and native FFI contract |
| [Afrowave civil-only licensing policy](licensing/AFROWAVE-CIVIL-ONLY-POLICY.md) | Approved ethics direction; legal text remains pending |
| [Risk-based AHPL precedent review](licensing/RISK-BASED-AHPL-REVIEW.md) | Why Textscape warrants additional protection; pitfalls of prior template |
| [Browser and JS adapters](architecture/BROWSER-RUNTIME.md) | Replaceable engines, DOM, rendering |
| [Workloads and background worker](architecture/WORKLOADS.md) | Durable tasks, monitoring, persistence |
| [Mail and notifications](architecture/MAIL-NOTIFICATIONS.md) | Textbird, badges, desktop/BEL |
| [AI and extensions](architecture/AI-EXTENSIONS.md) | Prompt packs, plugin trust, catalog |
| [Interface sketches](interfaces/CONTRACTS.md) | Illustrative APIs, not stable contracts |

## User features and security

| Document | Purpose |
| --- | --- |
| [TUI/UX](features/TUI-UX.md) | Tabs, status, activity pulldowns, F12 |
| [Localization](features/LOCALIZATION.md) | Translation-first UI, accessibility |
| [FactCheck and neutral language](features/FACTCHECK-LANGUAGE.md) | Claims, evidence, source independence |
| [Glass House](security/GLASS-HOUSE.md) | Transparency and data management |
| [Threat model](security/THREAT-MODEL.md) | Security principals, permissions and privacy |

## Process, testing and planning

| Document | Purpose |
| --- | --- |
| [Implementation status](../IMPLEMENTATION_STATUS.md) | Current verified work |
| [Development workflow](planning/DEVELOPMENT-WORKFLOW.md) | Requirement-to-code gates and ownership |
| [Requirements traceability](planning/REQUIREMENTS-TRACEABILITY.md) | Initial requirement IDs and test targets |
| [Test strategy](testing/TEST-STRATEGY.md) | Conformance and regression approach |
| [Roadmap](planning/ROADMAP.md) | Suggested development stages |
| [Open questions](planning/OPEN-QUESTIONS.md) | Unresolved decisions |
| [Decision log](decisions/README.md) | ADR index and decision status |
| [ADR 0001: Languages and interop](decisions/0001-rust-first-native-interop.md) | Accepted Rust-first direction |
| [ADR 0002: Civil-only policy](decisions/0002-afrowave-civil-only-policy.md) | Accepted restrictions; no operative LICENSE |
| [ADR template](decisions/0000-template.md) | Repeatable proposal/decision record |
| [Publishing notes](planning/PUBLISHING.md) | Historical initial-publication guide |

## Change discipline

Documentation is in English. Product UI strings must eventually be localizable. Use relative links for internal docs. A pull request must state which requirements, privacy flows, tests, status or decisions it changes; update affected docs in the same PR.

Keep exactly one canonical implementation status document and one canonical doc tree (`docs/`, lowercase). Do not create parallel `Docs/` and `docs/` paths because they conflict on common case-insensitive filesystems.
