# FactCheck, source lineage, language inspection and neutral rewrite

**Status:** proposed optional AI-supported feature, not an existing truth oracle.

## Principle: explain every claim

Reject vague outputs such as "the article is mostly true" or "other sources disagree". The report must state: **Article A claims X; source B documents Y; source C independently finds Z; the discrepancy is Q, because R.** Link to specific passages, publication dates, archived snapshots when permitted, and distinguish what each source independently establishes.

Claim-level statuses: supported, contradicted by cited evidence, partly supported, not independently verified, inconclusive, subjective opinion, ambiguous, or outside scope. Do not turn "X made an official statement" into "X's statement is true". Confidence or coverage must not masquerade as objective proof.

## Evidence lineage

Five outlets republishing one agency article are **one underlying information origin**, not five independent confirmations. Paraphrases and syndicated reports may share the same origin. Independently sourced first-hand records, documents, interviews and investigations should be represented separately. Independence attaches to an *individual claim*, not automatically to a publication's entire output. Uncertain attribution stays marked uncertain; do not guess.

Capture source URL, publisher, document type, author, time, relevant excerpt, acquisition/verification time, primary/secondary status, parent sources, evidence quality and unresolved conflicts. Present a navigable evidence graph and provenance for each conclusion. AI may propose lineage connections, but unsupported inference cannot turn into a declared fact.

## Chronology-first and symmetry-first

Reconstruct dates/actions/causal sequence, relevant omissions, initiators and consequences before making narrative-level judgments. Apply the same classification to equivalent actions independent of nationality, employer, ideology, or prestige. Language framing tests can swap actor identity while keeping the stipulated factual record invariant, then compare output; such tests diagnose inconsistency rather than proving intent of an author.

## Neutral language is not softened language

**Select the most accurate and strongest description that the evidence warrants**: no laundering of killings into "incidents", torture into "enhanced methods", or theft into "asset transfers" if the concrete acts are proved; equally never upgrade an unverified death into murder or state speculation as proven intent. Preserve identified actor, victim, intent, action, consequence, chronology and uncertainty where supported. Strongest means highest descriptive specificity/severity *that remains entailed by evidence*, not maximal emotional charge.

Different user profiles may prefer factual everyday wording, legal terminology, academic source attribution or custom rules. They may change vocabulary and degree of explanation, **not** secretly change the shared underlying evidence. A legal profile may require extra qualification of statutory elements; the ordinary reader may prefer accurate non-technical words.

Suggested output labels: "Confirmed by [specific evidence]:", "The author claims:", "According to [named source]:", "The author argues:", "Available evidence contradicts:", "Not independently verified:". Include the reason for each classification. Preserve the original text side by side with the derived rewrite, optionally with inline diff and links to each evidence item. No silent overwriting.

## Language and narrative manipulation

Inspect euphemism, loaded labels, selective chronology, passive voice hiding agents, unsupported certainty, opinion posed as fact, source amplification, asymmetrical naming of the same conduct. Findings must cite the actual wording and explain the effect; detecting a linguistic pattern does **not** by itself prove deliberate propaganda or author's intent.

Article composition statistics can show proportions of **counted claims** in defined categories (e.g. verified, opinion, unverified, contradicted). Specify the denominator; do not print a bogus universal "73% propaganda" metric. Offer alternatives such as text-span and claim-count shares with their limitations.

## FactCheck as a workload

User chooses a page, highlighted passage, author watcher or news workload. Pipeline: extract claims -> locate primary/independent sources -> trace lineage -> build chronology -> evaluate each claim -> explain language -> optionally generate neutral side-by-side rewrite -> persist evidence and alert on new findings. Recheck later with new evidence and keep version history. No article censorship or automatic removal from reading lists.

## Tests and safeguards

- Same event with swapped actors; no asymmetric euphemism.
- Correctly preserve harsh warranted wording; do not infer unproven crime/intent.
- One copied article on several sites stays one origin.
- Attribution versus fact distinction; unknown does not equal false.
- Claim-by-claim citations and exact contradiction descriptions.
- Date/chronology omission and repeated story cross-publication.
- Original immutable; changes traceable and reversible.
- Prompt injection in source text is ignored as instructions; local/remote model destination exposed.
- Tests must evaluate output against *specific fixtures and rubrics*, not naive regex word counts.
