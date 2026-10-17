# Architecture Decision Log

This is a **preliminary record of design intentions**, not a formal ratified ADR list. Each item should be converted into a dedicated dated ADR as decisions are validated.

| ID | Topic | Current status | Rationale |
| --- | --- | --- | --- |
| D-001 | Terminal-native frontend first | Proposed | Useful without GUI or powerful hardware |
| D-002 | Glass House transparent data model | Core principle | Owner can inspect/control data and actions |
| D-003 | Browser JS adapter API | Proposed | Replaceable engines, community additions, consistent tests |
| D-004 | Spec-linked conformance harness | Core principle | Exact evidence and immediate regressions |
| D-005 | Separate durable Workload Engine | Proposed | Tabs must not own jobs; background preparation |
| D-006 | Optional per-user Worker | Proposed | Startup preparation and notifications without UI |
| D-007 | Single Event/Notification Service | Proposed | Cross-module badges, sound and desktop integration |
| D-008 | Community prompt packs as plugins | Proposed | Reusable inspectable AI tasks with declared permissions |
| D-009 | FactCheck evidence lineage | Core principle | Syndicated duplicates count as one underlying source |
| D-010 | Evidence-bounded strongest accurate language | Core principle | Neither softening nor unsupported escalation |
| D-011 | AI has no arbitrary shell privilege | Core principle | User runs their own commands; isolated repair agent separately |
| D-012 | One owner for shared contracts / cautious parallelism | Core principle | Prevent race/conflicting changes; prioritize green tests |
| D-013 | Localization first | Core principle | English docs, localized interface and prompts |
| D-014 | License policy | **Unresolved** | Public repository is not automatically open-source licensed |

## ADR template

Create `NNNN-short-title.md` containing: context, options, decision, status, consequences, testing/rollback and date. Reject unverified claims and distinguish requirements from implementation choices.
