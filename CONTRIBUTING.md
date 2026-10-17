# Contributing — early design stage

Thank you for considering Textscape. At this stage we are recording and validating an initial architecture, **not reviewing ready-made implementations of every subsystem**.

## Valuable early contributions

- Pinpoint a standards requirement and provide a minimal executable test fixture.
- Compare potential DOM/layout/JS runtimes with reproducible measurements and licensing notes.
- Propose a narrowly scoped interface with lifecycle/error/resource semantics.
- Identify privacy/security blind spots, localization/accessibility needs or incorrect assumptions.
- Suggest a small vertical-slice prototype with measurable acceptance criteria.
- Improve docs by naming exact conflicts between decisions rather than silently resolving them.

Before making changes, read the [canonical implementation status](IMPLEMENTATION_STATUS.md), [documentation index](docs/README.md), [development workflow](docs/planning/DEVELOPMENT-WORKFLOW.md), and [requirement matrix](docs/planning/REQUIREMENTS-TRACEABILITY.md). A documented feature is not an implemented feature.

## Proposed contribution workflow

1. Open an issue explaining user value, supporting standards/evidence and scope.
2. For shared interfaces, seek a single agreed design owner before implementation.
3. Add tests or reproducible fixtures first; separate actual test runs from proposed expectations.
4. Make a small change on a feature branch; do not modify unrelated modules.
5. Run the appropriate suite and document results. No "all green" claim unless run.
6. Update `IMPLEMENTATION_STATUS.md` and requirement evidence if the change affects project maturity; distinguish tests that were run from those planned.
7. Submit PR with data flow/permissions/localization impact, risks and fallback.

Do not include credentials, personal information or private mail in public issues or reports. All proposed AI-generated code requires independent review.

**The licensing policy is chosen, but the legal license text is not finalized.** Textscape intends an [Afrowave Civil-Only ethical policy](docs/licensing/AFROWAVE-CIVIL-ONLY-POLICY.md) with broad civilian rights and excluded military, law-enforcement, intelligence and repressive uses. It is not an OSI Open Source license. Do not import substantial external code before a finalized license and contribution policy are published; original upstream licenses remain in force.
