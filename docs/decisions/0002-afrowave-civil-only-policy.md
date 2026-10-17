# ADR 0002 — Afrowave civil-only ethical licensing direction

- **Status:** Accepted policy direction; **binding license text pending**
- **Date:** 2026-10-17
- **Related requirements:** TS-LIC-001, TS-SEC-001
- **Implementation:** No LICENSE adopted and no production code shipped

## Context

The project owner requires broad freedom to inspect, modify, use and share Textscape **for civilian purposes**, without fee-based or political selection of ordinary users. The owner expressly rejects military, police/law-enforcement, intelligence and repressive-sector uses anywhere, including indirect application through intermediaries. These are use-based ethical constraints, not browser-side permission rules.

The restriction cannot be described as OSI-open-source licensing. Existing libraries remain governed by their upstream licenses.

## Decision

Document and pursue an **Afrowave Civil-Only ethical source-available license** for Afrowave-owned code and releases. Its design must allow normal civilian use, modification, commercial use and redistribution while prohibiting military and repressive exploitation, including prohibited end beneficiaries. **Do not publish an unreviewed LICENSE or assert that this draft already grants rights.**

## Alternative approaches

1. **MIT/Apache-2.0/other OSI permissive license:** excellent ecosystem interoperability, but legally cannot impose the desired civil-only exclusions. Rejected as the sole Afrowave-owned code license.
2. **Standard OSI copyleft license:** also disallows the requested discrimination/field-of-use restriction; incompatible with the stated goal if used alone.
3. **Custom ethical source-available license:** matches the stated owner intent, but has greater legal-review, adoption, compatibility and enforceability costs. **Selected direction; text unresolved.**
4. **OSI license plus voluntary ethics pledge:** may communicate values but would not enforce the exclusion. Not an equivalent substitute.

## Risk proportionality and existing AHPL precedent

Textscape's author-monitoring, aggregation and background AI tools make repression and targeting misuse unusually foreseeable. The chosen protection is **project-specific** and does not automatically amend other Afrowave software licenses (for example, already distributed MIT utilities). Afrowave's existing AHPL v1 is a reference, not text adopted by this ADR. Its wording must be assessed to avoid banning normal civilian monitoring of published articles, and its penalty clauses must be independently reviewed for enforceability. See [risk-based AHPL review](../licensing/RISK-BASED-AHPL-REVIEW.md).

## Consequences

- Public repository != unrestricted reuse.
- Accurate terminology in all documents and package metadata.
- Versioned notices and contributions policy are prerequisites to significant contributions or binary redistribution.
- Assess MIT/BSD/MPL/GPL third-party dependencies separately; no retroactive restriction on upstream rights.
- **Accepted humanitarian exception principle:** individually considered, explicit, incident-specific, purpose-limited, temporary approval may be granted for lifesaving disaster/rescue activity even when otherwise excluded military units assist. No general military license, implicit consent, or allowed secondary intelligence/repressive use. See [exception policy](../licensing/HUMANITARIAN-EXCEPTIONS.md).
- Final humanitarian exception instrument, remedies, specific covered institutions and global enforceability require dedicated legal drafting.
- The license should not depend on unidentified persons/groups getting informal permissions to do ordinary civilian tasks.

## Verification and status

- No license is finalized; implementation and compliance tests NOT_RUN.
- Audit README/CONTRIBUTING/status for no false claims of an operative OSI license.
- Prior to release, require legal review and a documented dependency compatibility report.

Policy details: [Afrowave Civil-Only Licensing](../licensing/AFROWAVE-CIVIL-ONLY-POLICY.md).
