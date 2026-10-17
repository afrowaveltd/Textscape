# Humanitarian Emergency Exceptions — Civil-Only License Policy

> **Accepted policy principle (2026-10-17):** humanitarian necessity may justify an individually reviewed, temporary, purpose-specific exception, even if military personnel participate in the rescue.  
> **Status:** policy design; **NOT a license, not a standing exception, and not an issued authorization**. Legal terms, approval authority, safeguards and exact documentation remain to be finalized.

## Purpose

Afrowave's civil-only restriction is meant to prevent its technology from facilitating violence, coercion or persecution — **not** to obstruct immediate action to save people. For example, Textscape could help authorized responders find people missing after a flood or earthquake by collecting verified public requests, coordinating civilian information and supporting rescue communications. If the armed forces are legitimately assisting emergency services, Afrowave may consider allowing **only the relevant humanitarian operation**.

**No organization is automatically entitled to a license because it declares its purpose humanitarian, military-defense-related, urgent or lawful.** The exceptional permission must be approved individually and explicitly.

## Exception principles

1. **Individual assessment:** a concrete documented request, named applicant and identified authorized operating parties; examine actual purpose, affected civilians, known risks and feasible civilian alternatives.
2. **Strictly humanitarian objective:** saving lives, locating missing people, providing immediate medical/disaster relief, facilitating rescue or protecting people from imminent serious injury. Participation of an otherwise excluded entity does not itself invalidate a request.
3. **Specific permitted functions:** identify the Textscape components, datasets and workflows required for the rescue, not a general license to the entire platform.
4. **Time and geographic/incident limits:** record an explicit start and expiry, incident reference and relevant area where appropriate. Extensions require independent review and renewed approval.
5. **No conversion into repression:** no use for combat operations, target selection, intelligence collection, coercive profiling of civilians, political monitoring, arrests, or monitoring journalists/dissidents. No secondary use of data for those purposes.
6. **Named recipients, no onward transfer:** the grant is bound to named personnel/units/systems and eligible contractors acting solely on the authorized operation; no sublicensing, reassignment or unrelated deployments.
7. **Data protection:** minimize information about missing people and relatives; use appropriate access control, retention and deletion rules, and avoid publishing personal details in any public register.
8. **Transparent authorization:** use a dated, versioned, uniquely identified and authenticable written grant; record the approving authority, scope, requester, conditions, expiry and revocation rules. Publish a **privacy-safe summary where appropriate**, withholding operational or survivor details that might endanger people.
9. **Audit and accountability:** allow proportionate verification against the written grant. **Do not require secret application telemetry, backdoors, or generalized monitoring of civilian users** as an enforcement mechanism.
10. **Suspension/revocation:** material misrepresentation, scope creep or harmful repurposing makes the exemption subject to suspension/revocation under terms to be legally defined. Where feasible, arrange a safe handover so enforcement does not unnecessarily endanger people currently being rescued.

## Example — earthquake search and rescue

A region suffers a destructive earthquake. Civilian rescue coordinators request use of a Textscape workload to aggregate trusted reports of missing people, organize location leads and notify rescue teams. Military helicopters and logistics units are assisting the rescue.

**Illustrative permissible authorization:** one named emergency response operation; only approved data collection and rescue coordination features; named responders and the military rescue/logistics units assisting them; fixed short validity period; strict civilian-data handling, no unrelated investigations or surveillance, and renewal only after explicit reassessment.

**Not permitted under that grant:** reusing the collected names or locations to create political profiles, identify opposition supporters, assist targeting, monitor journalists or run intelligence operations, even while the same institution continues participating in disaster relief.

This is an **example**, not a real permission or an executable license.

## Proposed exception record — fields, not a final legal form

```text
Exception ID / issue date / license policy revision
Requesting entity and responsible contact
Authorized implementing entity/unit(s) and service providers
Emergency/incident and verified humanitarian need
Permitted Textscape versions, components and workflows
Permitted data categories, sources and destinations
Area and operational environment, if relevant
Start and expiry, renewal procedure
Explicitly prohibited secondary uses
Privacy, retention, deletion, transparency and audit conditions
Signatory/approval evidence and authenticity verification
Suspension/revocation, notifications and safe wind-down terms
```

## Legal and product boundary

- **This policy cannot change upstream licenses** for third-party engines and libraries.
- No final license or approval has been issued. The Afrowave Civil-Only policy remains the default, with exemptions **only when specifically issued**.
- Qualified legal review must establish authorizing authority, a valid mechanism for separate permissions, limits on disclosure and audit, emergency speed, revocation and local enforceability.
- The aim is consistent treatment of comparable **rescue circumstances**, not privileged treatment of any particular state, army or political actor.

See [Civil-Only Policy](AFROWAVE-CIVIL-ONLY-POLICY.md), [ADR 0002](../decisions/0002-afrowave-civil-only-policy.md), [Threat Model](../security/THREAT-MODEL.md), and [Implementation Status](../../IMPLEMENTATION_STATUS.md).
