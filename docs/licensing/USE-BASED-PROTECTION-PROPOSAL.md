# Use-Based Protection and Defense Harm Reduction — Policy Refinement

> **OWNER'S REFINEMENT UNDER DISCUSSION — NOT YET RATIFIED AS THE FINAL LICENSE SCOPE (2026-10-17).**
> This design note explores a change to the earlier categorical institutional exclusions in [ADR 0002](../decisions/0002-afrowave-civil-only-policy.md). It is not an operative license, legal advice, exception, or permission grant. **Do not interpret this proposal as currently authorizing use by any otherwise excluded entity.**

## The owner's distinction

Two related principles must be distinguished:

1. **Absolute prohibition of repressive use:** No Afrowave-owned software may be licensed for use **serving the repression, persecution, intimidation or coercive targeting of individuals, communities or groups**, including political, cultural, professional and interest groups, under **any exception**. Invoking a criminal investigation, prosecution, national-security law or a label such as "terrorist" does **not** by itself establish permissibility or exempt the actor from the restriction. Criminalization of dissent can be used to justify repression.
2. **Potentially legitimate protective use:** A country under attack might need software to **save lives, warn people, support evacuation, coordinate relief or otherwise minimize harm**. That purpose is distinguishable from retaliation, offensive harm, coercive targeting or persecution. The fact that a government, army or emergency agency is involved should trigger careful scrutiny but not automatically turn a life-saving task into repression.

This proposal shifts emphasis from **who operates the software** to **what it is demonstrably used to do, who benefits, whom it can harm, and what happens to the data**. The owner has **not yet settled whether some institution-level bans should remain unconditional in addition to a purpose-based prohibition**; that conflict must be resolved explicitly before writing a binding license.

## Illustrative decision matrix — not grants or legal verdicts

| Scenario | Preliminary treatment | Why / boundary |
| --- | --- | --- |
| A civilian follows the public articles of a journalist | Ordinary civil use | Reading or research is not persecution by itself |
| A rescue team uses Textscape to organize missing-person reports after an earthquake; military logisticians assist | Candidate for a narrow, individually approved humanitarian exception where required | Scope must be rescue-only, time-limited, privacy-protective; not reusable for intelligence or repression |
| An attacked state's civil protection service aggregates verified shelter and evacuation notices | Candidate for protective use, subject to final entity rules | Aim and result are harm reduction, not retaliatory targeting |
| A public agency uses data to warn civilians about damaged infrastructure or an approaching hazard | Candidate for protective use | Do not infer broader surveillance, military intelligence, combat or enforcement rights |
| A security service collects journalists' articles to build profiles for questioning, intimidation or arrests | Prohibited repressive use without exception | Public-source content and a legal label do not sanitize coercive targeting |
| A state labels a dissident a terrorist and uses Textscape to facilitate persecution | Prohibited repressive use without exception | A state's legal designation is not dispositive evidence of humane or non-repressive conduct |
| An attacked state uses Textscape analysis to choose targets for retaliation or harm against people | Prohibited purpose under the proposed rule | An initial attack does not convert retaliation into protective civilian data processing |
| A lawful nonpolitical criminal investigation uses Textscape for unrelated ordinary evidence work | **Unresolved** | Define the conduct-based boundary precisely; formal lawfulness alone is insufficient, and not every criminal procedure necessarily constitutes repression |
| Dual-use situational awareness that may support both evacuation and military targeting | **Unresolved / require narrow task and data separation** | Do not treat a defensive label as automatic authorization; evaluate downstream uses and enforceable scoping |

## Proposed license drafting requirements

- A clear **non-derogable anti-repression clause**: no emergency, official order, criminal-law label, government designation, claimed legitimacy or individually granted humanitarian exception may authorize repression of a person or group.
- Define prohibited **actions**, **beneficiaries**, **outcomes** and **secondary uses** concretely: coercive profiling, persecution of dissent, intimidation, arbitrary deprivation of liberty, targeting people for punishment, and transfer of data for those purposes. Avoid vague language that indiscriminately forbids normal public-interest research.
- Define **protective harm reduction** narrowly, with emphasis on preservation of life, evacuation, disaster response, medical care and civilian infrastructure restoration. A general claim of self-defense must **not** create a blanket authorization for combat, intelligence, retaliation or targeting.
- State whether institution-level prohibitions (military, law enforcement, intelligence, etc.) remain absolute, are qualified only by an individual written exception, or are replaced in part by a purpose-based test. **This is an explicit open decision.**
- Keep the existing **written, individually reviewed, purpose-specific, time-limited humanitarian exceptions** for otherwise excluded recipients unless and until superseded by an approved license model. No exemption can override the anti-repression prohibition.
- Evaluate contractor intermediaries and data re-use, including whether a benign primary task feeds repressive downstream systems.
- Document who may grant exceptions, how claims are verified, expiration/renewal, revocation, data retention and auditable limited-purpose compliance, **without covert telemetry**.
- Have counsel review legal definitions, standing, jurisdiction, sanctions, compatibility with third-party dependencies, and objective evidence needed to distinguish legitimate policing from political repression.

## How to verify proposed boundaries

Draft adversarial cases and compare identical conduct across countries and institutions. Inputs/expected classifications must be reviewed and transparent; no unreliable AI-only policing of users. Examples: an article watcher used for private reading versus one feeding an arrest list; a civil-defense evacuation feed versus a retaliatory targeting feed; a missing-person rescue case versus covert political-profiling reuse; a prosecution label without factual proof of harmful conduct.

No code, enforcement system, tests, legal instrument or permissions have been implemented under this proposal.

See [Civil-Only Policy](AFROWAVE-CIVIL-ONLY-POLICY.md), [Humanitarian Exceptions](HUMANITARIAN-EXCEPTIONS.md), [Risk-based licensing](RISK-BASED-AHPL-REVIEW.md), [Threat Model](../security/THREAT-MODEL.md), and [Open Questions](../planning/OPEN-QUESTIONS.md).
