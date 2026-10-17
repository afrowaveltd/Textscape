# Security boundaries and threat model (draft)

## Principal identities

- **Local user/owner:** may inspect and control Textscape-managed data and configuration according to OS account rights.
- **Web origin/page JavaScript:** confined to browser security policies including same-origin restrictions, CSP/sandbox behavior where implemented, permissions, no OS shell exposure.
- **Plugin:** scoped, separately identified, audited capability principal; prompt-pack plugins are *instructions*, not authority.
- **AI agent:** explicit data/tool permissions, no ambient raw filesystem, credentials, arbitrary commands or bypassing approval. Prompt injection from pages, email and search results is untrusted content, not new instructions.
- **Worker:** a per-user process with authenticated IPC, not automatic root/admin; may need narrower privileges than the interactive UI.
- **Remote service:** may receive only data needed for an explicitly approved configured function; remote storage outside user's computer cannot be guaranteed removable.

## Key risks to prototype and test

- JS engine RCE, prototype pollution, host object use-after-free, GC rooting/tracing, async race, cross-origin leakage.
- Parsing hostile HTML/CSS, untrusted email MIME, PDFs/attachments, image decoders, malformed RSS and repository metadata.
- Token/cookie leakage through logs, automatic fact-check prompts, third-party URL reputation lookups, error report uploads.
- Indirect prompt injection via page text/email/plugin-provided prompt; never confuse webpage text with user instructions.
- Community plugins requesting suspicious permissions, malicious update, source substitution, dependency abandonment.
- Accidental shared mutable app state and worker double execution; scheduler races and repeated sends.
- Misleading phishing 'safe' results, unverifiable fact-check verdicts, falsely claimed independent sources.

## Link inspection

Layer 1: offline URL parsing, actual registrable domain, IDN/confusable hostnames, displayed-target mismatch, suspicious redirects encoded in URL. Layer 2: optional known-threat reputation connectors with transparent privacy characteristics and licensing. Layer 3: optional AI analysis of context, with strict authorization before sending potentially sensitive URLs/tokenized links. Do not auto-open a suspicious URL just to inspect it; a sandboxed fetch must not receive session secrets. An empty threat database result is not proof of safety.

## Community extension review

Manifest declarations; static validation; malicious instruction/prompt injection tests; permission-diff disclosure on upgrade; immutable releases and hashes/signatures; provenance and test reports. Reviewed means reviewed under defined criteria, **not** immune to abuse. User grants remain independent of catalog approval.

## Optional incident reporting and patch proposal

Runtime error -> structured diagnostic -> related regression test -> owner-visible exact report -> permission to send -> deduplicate -> independent repair agent in isolated worktree -> reproducible failing test -> patch -> full regression tests -> human review -> pull request. Agent does not self-deploy production changes or gain shell on users' devices. Keep audit records and avoid disclosing personal or source secrets through public GitHub issues.

## Coercive surveillance and repression: explicit misuse threat

Textscape combines source monitoring, author identity records, long-running watchers, content collection, search, notification, optional AI classification and structured exports. These capabilities can serve legitimate readers and researchers, but may also be repurposed by military, police, intelligence organizations or coercive regimes to **identify and track journalists, dissidents, organizers, critics or other targeted people**. This is a first-class misuse scenario, not a theoretical afterthought.

### Distinguish intent, capability and authority

- **License/policy boundary:** the project owner intends to deny licensing of Afrowave-owned Textscape code for military, police, intelligence and repressive uses, including work by third-party contractors on their behalf. The specific license text is pending; a license cannot technically prevent a determined unauthorized fork.
- **Product security boundary:** no remote authority or Afrowave operator obtains surveillance access to a user's local profile merely by providing software or update infrastructure. No hidden telemetry, reporting of watched authors, central tracking, unsolicited upload of monitoring lists or backdoors.
- **User sovereignty boundary:** ordinary civilian users retain control over their own reading lists, author watchers, plugins and data. Do not secretly disable legitimate features or claim to determine a person's political legitimacy.
- **Agent/plugin boundary:** third-party agents and extensions receive only declared, user-authorized data and tools; never share all author identities, correspondence, contacts or full reading history as an ambient permission.
- **Distribution boundary:** audit third-party dependencies, compiled artifacts, license notices, plugin catalog and contribution paths; do not claim an ethical use restriction carries over to independent MIT/BSD/MPL/GPL upstream projects.

### Design mitigations to evaluate and test

1. **Local-first sensitive state:** author identity lists, watch histories, email and private analytics should remain local by default, without compulsory central service accounts.
2. **Explicit outbound payloads:** any share/sync/AI work/report includes a complete, inspectable destination and payload; no hidden background transfer of watchlists or other personal profiles.
3. **Constrained, auditable automation:** purpose-specific capabilities, rate limits and operation history for bulk extraction/export, agent execution and external connectors. Constraints must not silently remove legitimate owner access.
4. **No covert surveillance features:** do not implement hidden stalkerware interfaces, covert endpoint monitoring, stealth capture of third parties, or privileged bypasses under an innocent "watcher" label.
5. **Sensitive-data minimization:** retain only what a user needs, separate public articles from private correspondence, encrypt secrets as appropriate, and enable inspect/export/erase. Logs should avoid unnecessary personal identifiers.
6. **Public catalog review:** assess community watchers and prompts for covert profiling, prohibited beneficiaries, undisclosed transmission and attempted permission expansion before inclusion in the official catalog.
7. **Auditable boundaries:** include tests asserting that watching public author articles does not silently send the list of authors or collected history to Afrowave or other providers; watch identity, local data and external requests must be visible in Glass House.
8. **No safety absolutism:** public information and open source are inherently reusable outside the project's control. Ethics terms, catalog governance, transparency and product design reduce facilitation but cannot guarantee that a hostile actor will not misuse knowledge or code.

### Example abuse case

An unauthorized repressive organization modifies a community "Author Watcher" pack to compile a named list of journalists and notify an external intelligence endpoint when any publish a new article. The official Textscape project should neither license that use nor distribute a connector designed for it. A legitimate citizen tracking public authors should, however, remain able to use private on-device monitoring without an opaque central permission system.

Security test requirements for outbound data transparency, plugin capability boundaries, local-first storage and official catalog moderation must be tracked in [Requirements Traceability](../planning/REQUIREMENTS-TRACEABILITY.md). See the [Civil-Only policy](../licensing/AFROWAVE-CIVIL-ONLY-POLICY.md).

## Open issues

Browser-origin sandboxing, remote debugging security, crypto/storage secret protection, actual TLS/certificate stack choices, crash isolation, signed update mechanism, precise permissions syntax, responsible disclosure process, CI secret handling.
