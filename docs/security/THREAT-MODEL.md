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

## Open issues

Browser-origin sandboxing, remote debugging security, crypto/storage secret protection, actual TLS/certificate stack choices, crash isolation, signed update mechanism, precise permissions syntax, responsible disclosure process, CI secret handling.
