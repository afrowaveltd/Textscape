# Contributing — early design stage

Thank you for considering Textscape. At this stage we are recording and validating an initial architecture, **not reviewing ready-made implementations of every subsystem**.

## Valuable early contributions

- Pinpoint a standards requirement and provide a minimal executable test fixture.
- Compare potential DOM/layout/JS runtimes with reproducible measurements and licensing notes.
- Propose a narrowly scoped interface with lifecycle/error/resource semantics.
- Identify privacy/security blind spots, localization/accessibility needs or incorrect assumptions.
- Suggest a small vertical-slice prototype with measurable acceptance criteria.
- Improve docs by naming exact conflicts between decisions rather than silently resolving them.

## Proposed contribution workflow

1. Open an issue explaining user value, supporting standards/evidence and scope.
2. For shared interfaces, seek a single agreed design owner before implementation.
3. Add tests or reproducible fixtures first; separate actual test runs from proposed expectations.
4. Make a small change on a feature branch; do not modify unrelated modules.
5. Run the appropriate suite and document results. No "all green" claim unless run.
6. Submit PR with data flow/permissions/localization impact, risks and fallback.

Do not include credentials, personal information or private mail in public issues or reports. All proposed AI-generated code requires independent review.

**Licensing for contributions remains undecided**. Do not contribute substantial third-party code until a license and contributor policy have been explicitly chosen and published.
