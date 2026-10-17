# Afrowave Civil-Only Licensing — Project Policy and Drafting Requirements

> **Policy direction accepted by the project owner, 2026-10-17.**  
> **NOT AN OPERATIVE SOFTWARE LICENSE. NOT A LICENSE GRANT.**  
> Final license legal wording, enforcement model, exception authority and third-party compatibility require a dedicated review before publishing `LICENSE` or licensing contributions/releases.

## Objective

Textscape should be **publicly readable, modifiable, forkable, sharable and freely usable for civilian purposes**, including personal, educational, research, non-profit and commercial work, without discrimination among ordinary civilian users. No general fee or mandatory permission should be needed for ordinary civil use.

A central Afrowave requirement is that **the project and Afrowave-owned code must not be licensed for military, policing, intelligence, surveillance/repression or comparable coercive uses anywhere in the world**. A country, alliance, supplier or political affiliation does not receive an exemption merely through its identity.

## Intended prohibited recipients / uses

The finalized terms must address **direct and indirect** usage, modifications, derivative works, distribution and use through intermediaries or contractors **on behalf of or for the benefit of**:

1. Armed forces, military commands, defense operations and combat/weapon systems.
2. Police, law-enforcement and comparable coercive security services.
3. Intelligence, secret services, covert surveillance and security agencies.
4. Border enforcement, paramilitary and other governmental or quasi-governmental organizations carrying out coercive or repressive activities.
5. Contractors and intermediaries **when acting for the prohibited purpose or beneficiary**, rather than treating an entire civilian firm as inherently prohibited for unrelated civilian work.

The exact definitions of organizations, operations, enforcement, edge cases and the treatment of lawful civilian branches need legally precise drafting. There must be no state-specific loophole. Textscape should not be used as a tool for repression of people.

## Permissions intended for eligible civilian users

- Use and run the software for any lawful civilian task, including commercial applications.
- Read, inspect, study and modify Afrowave-owned source.
- Share original and modified versions subject to attribution/notices and the finalized civil-only restrictions.
- Build community plugins and adapters subject to their own correctly disclosed rights and obligations.
- Choose local/remote AI, privacy configuration and extensions without hidden vendor controls.

These are the **intended permissions**, not yet rights conferred by an executable legal instrument.

## Explicit licensing accuracy

- This policy restricts particular classes of use and organizations. It therefore **does not qualify as OSI Open Source**, whose definition forbids discrimination against fields of endeavor and groups. Use **public-source / source-available under an ethical civil-only license** once final terms exist; do not mislabel as OSI-approved open source.
- A public GitHub repository, visible source, draft policy or ethical notice does **not** by itself supply a reusable software license.
- **Upstream source keeps its original license.** MIT, BSD, MPL, GPL and other dependencies cannot have Afrowave restrictions attached to their upstream rights by declaration. Some copyleft integrations or redistribution forms may prohibit additional use restrictions. Verify every candidate engine and distribution model *before* integrating it.
- Do not automatically assert that the policy legally binds every recipient who merely reads the public repository, or that a restriction is globally enforceable.
- Clearly separate Afrowave-owned copyright from third-party code, fixtures, generated sources, bundled binaries, icons and community contributions. Keep SPDX notices and a license/SBOM inventory.

Relevant references:
- [Open Source Definition](https://opensource.org/osd) (especially clauses 5 and 6)
- [OSI FAQ on field-of-use restrictions](https://opensource.org/faq)
- [Architecture language choices](../architecture/LANGUAGE-AND-FFI.md)

## Humanitarian exceptions and enforcement — drafting topics, not automatic rights

The Afrowave civil-only model has contemplated **exceptional, temporary, purpose-limited humanitarian authorization** for urgent life/health or disaster relief. Any such exception must be explicitly granted by the responsible Afrowave authority, narrowly scoped, revocable and documented; no default authorization exists.

Potential contractual penalties, calculation tied to national GDP, recipients of remedies, voting/approval thresholds and enforcement jurisdictions are **not finalized in this repository**. Do not silently invent thresholds or place unreviewed penalty text in a binding license. Any penalty must be separately assessed for legal enforceability and proportionality by qualified counsel.

## Before publishing a LICENSE

1. Draft definite legal terms for grant, restricted uses, covered parties, notice, modification and redistribution, survival/termination, exceptions, warranties, liability and jurisdiction.
2. Resolve ambiguous dual-use cases and treatment of government civilian institutions, contractors and emergency responders.
3. Agree on contribution terms so contributors knowingly license their own work under the same policy.
4. Audit all dependencies and licenses; decide what remains a separately licensed component, linked binary, IPC service or external program.
5. Obtain appropriate legal review; adopt and publish a versioned final license with a copyright/attribution policy.
6. Reflect final terms in README, CONTRIBUTING, package metadata, plugin SDK and releases.

**Decision boundary:** the civil-only **intent** is approved; the finalized legal instrument is **not** yet adopted.

See [ADR 0002](../decisions/0002-afrowave-civil-only-policy.md), [open questions](../planning/OPEN-QUESTIONS.md), and [implementation status](../../IMPLEMENTATION_STATUS.md).
