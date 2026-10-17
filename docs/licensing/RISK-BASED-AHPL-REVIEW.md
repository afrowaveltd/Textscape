# Risk-based licensing and AHPL precedent — Textscape

> **Draft legal/architectural assessment, 2026-10-17. Not an operative license, legal opinion or permission grant.**  
> The project owner approved evaluating Afrowave licensing **per project's realistic misuse potential**, rather than indiscriminately assigning the most restrictive license to every Afrowave tool. This document does not reproduce or publish the complete text of any internal Afrowave repository's existing license.

## Why Textscape warrants heightened licensing precautions

Textscape intends to provide durable author/article watchers, multi-site news collection, AI categorization and fact checking, background execution, configurable prompt plugins and exportable reports. These capabilities can empower civilian readers and investigators; they could also enable coercive institutions to monitor **journalists, human-rights defenders, dissidents and other targeted people**, correlate their publications, or accelerate punitive action.

The motivating threat is **a repressive government, military/intelligence body, law-enforcement agency or contractor using Textscape's public-author-monitoring features to target people**. Risk assessment concerns actions and end beneficiaries, not nationality, politics or the identity of a particular state.

An ordinary civilian monitoring newly published articles of a favorite journalist **must remain allowed**. Legitimate public-document research, education, personal reading, analysis and journalism must not be silently prohibited by an imprecise blanket restriction against all "monitoring" or "surveillance."

## Risk-calibrated policy across Afrowave tools

- **General-purpose low-abuse-risk utilities:** may use ordinary permissive licenses where approved by the respective project owner; a civil-only direction for Textscape does not retroactively affect those licenses.
- **General-purpose libraries and formats:** assess plausible military/coercive use, dependency ecology and interoperability individually.
- **High-misuse-risk automation/monitoring systems such as Textscape:** require an explicit Afrowave Civil-Only ethical licensing strategy, clear prohibited beneficiaries and purposes, and supporting privacy-by-design safeguards.
- **Each repository owns its licensing decision.** Do not automatically extend an AJIS/Textscape restriction to every Afrowave repository without review.

A source-available civilian-only license is **not OSI Open Source** because of restrictions on beneficiaries/fields of use. Existing MIT/BSD/GPL/MPL dependencies retain their own grants and obligations.

## Prior Afrowave AHPL v1 — internal template assessment

An Afrowave project already contains an **Afrowave Humanitarian Protective License (AHPL) v1**. It supplies a precedent for:

- broad freedoms for eligible civilian use, modification, study and sharing;
- explicit exclusion of armed forces, police/law enforcement, intelligence and coercive/repressive state entities;
- indirect-use coverage for contractors and intermediaries acting for excluded beneficiaries;
- prohibited harmful purposes including political repression and invasive surveillance;
- narrow humanitarian emergency exception structure;
- attribution, enforcement and remedies topics.

**Do not copy AHPL v1 verbatim into Textscape's `LICENSE` at this stage.** In particular, the prior template has provisions needing legal review before reuse:

1. **Overbroad surveillance wording:** a general ban on watching individuals/groups risks encompassing legitimate civilian author/article watches. Prohibited use should be tied to coercive targeting, intimidation, persecution, human-rights abuse or an excluded institutional beneficiary. Decide separately what other forms of privacy-invasive profiling to ban.
2. **Penalty feasibility:** large state-GDP-indexed liquidated damages and automatic escalation should not be represented as inevitably binding or enforceable; validate proportionality, actual harm/causation, jurisdiction, standing, sovereign immunity and governing law with counsel.
3. **Vague ethical override:** the phrase "ethically questionable" alone does not define a sufficiently predictable license condition. Specify prohibited conduct/beneficiaries and a fair, reviewable authorization mechanism.
4. **Acceptance, termination and remedies:** mere publication or use does not guarantee enforceable assent or access to remedies in every jurisdiction. Draft the actual legal grant, restrictions, termination, attribution and enforcement procedure.
5. **Humanitarian exception:** preserve the ability to grant narrowly scoped, time-limited and documented emergency exceptions, subject to owner approval and consistent application; do not automatically infer an exception from an actor's self-description.
6. **Third-party rights:** full restrictions cannot be retroactively imposed on independently licensed dependencies. Copyleft-compatible packaging and linking need an explicit audit before choosing engines and distributing combined binaries.
7. **Civilian freedom:** avoid restricting peaceful individual reading, research, publication-monitoring, open-source contribution or legitimate civil-rights investigation simply because it uses the same underlying watch technology.

## Draft risk model (qualitative; not measured)

| Function | Legitimate use | Foreseeable misuse | Required review |
| --- | --- | --- | --- |
| Browser + basic navigation | Private browsing | Data capture | Standard browser sandbox and privacy |
| News aggregation | Personal reading | Mass collection for coercive profiling | Local-first state, documented sources, no covert exports |
| Author Watcher | Follow published articles | Track journalists/critics to facilitate retaliation | Strict no-hidden-upload policy, plugin review, beneficiary/use-based licensing |
| AI analysis and summarization | Evidence-based reading | Automated targeting classifications | Scope-limited tools, audit, prompt-injection tests, no unauthorized bulk export |
| Background Worker | Convenient feed/mail updates | Persistent unattended collection and transmission | Per-user authorization, identifiable tasks, execution and outbound logs |
| Community Watcher/Prompt Pack | Customized workflows | Malicious monitoring connector | Provenance review, explicit permissions, independent approval of sensitive data transfers |

## Scope of safeguards and honest limitations

Use **layered safeguards**, not a claim of perfect technological prevention:

1. License/prohibitions for Afrowave-owned source; contractual and enforcement assessment.
2. Official plugin/catalog policy: reject packages explicitly designed to target or profile people for repression.
3. Glass House: locally inspectable monitoring and explicit outbound payloads; no undisclosed Afrowave tracking of user watchlists.
4. Sandboxed agents/plugins, bounded permissions and non-bypassable user-authorization controls in the supported implementation.
5. Tests for unexpected exfiltration and privilege escalation; test cases must not require real journalists' private data.
6. Transparent source distribution and reproducible builds, within legal and dependency limits.

A determined hostile actor can modify and misuse accessible code outside the project's control. Neither a license nor UI safeguards alone can guarantee prevention. Avoid secret backdoors, political screening of regular users or central surveillance in the name of preventing surveillance.

## Decisions and gates

- **Accepted:** licence protection is proportional to project misuse risk; Textscape is treated as high risk; user/civilian access remains broad; institutional military/police/intelligence/repression uses should be excluded.
- **Reference only:** AHPL v1, without blanket adoption or republication.
- **Open:** exact covered entities, employee/contractor tests, precise prohibited conduct, exceptions, remedies, governing law, contributions, dependencies and product packaging.
- **Not completed:** final `LICENSE`, legal review, implementation, security tests.

References: [Civil-Only Policy](AFROWAVE-CIVIL-ONLY-POLICY.md), [ADR 0002](../decisions/0002-afrowave-civil-only-policy.md), [Threat model](../security/THREAT-MODEL.md), [Implementation status](../../IMPLEMENTATION_STATUS.md).
