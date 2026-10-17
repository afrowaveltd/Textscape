# Open questions and decisions not yet made

These are deliberately **not** answered by this first documentation commit.

1. **License wording and compatibility (policy already accepted):** Afrowave Civil-Only usage restrictions are an approved project direction, not a vague possibility. Finalize a legally reviewed custom license, covered military/police/intelligence/repressive uses, **the legally operative form of the already accepted individual humanitarian rescue exception** (including authority, time/mission limits, protected data, approval speed and revocation), enforcement definitions, contribution agreement and upstream dependency compatibility. See [Humanitarian Emergency Exceptions](../licensing/HUMANITARIAN-EXCEPTIONS.md). Do not call this OSI Open Source or treat the draft as an operative grant. See [policy](../licensing/AFROWAVE-CIVIL-ONLY-POLICY.md) and [ADR 0002](../decisions/0002-afrowave-civil-only-policy.md).
2. **Final name / repository slug / trademark:** Textscape Navigator, Textbird, "The Web. No Desktop Required." and a distinct 'T' icon are working branding.
3. **Engine/runtime implementation under accepted language allocation:** Rust is the default Textscape-owned implementation language; C-compatible ABI and narrow C/C++ adapters are the accepted native interoperability direction. Open questions are which DOM/layout/JS engines to select, exact boundary and process isolation, ABI specification, dependency licensing and measured footprint. See [languages](../architecture/LANGUAGE-AND-FFI.md) and [ADR 0001](../decisions/0001-rust-first-native-interop.md).
4. **Scope of engine interchangeability:** native plugin ABI versus process boundary and GC/DOM binding semantics; identify unavoidable engine-specific affordances.
5. **Web standard coverage:** which APIs and conformance cases gate the first usable preview, and how should terminal-only presentation differences be evaluated?
6. **Persistence:** exact store technology/schema migrations/encryption, storage partition model, backups and deletion semantics.
7. **Default privacy profile:** balance compatibility, blocking, reveal screens and clear metadata while never silently over-sharing.
8. **Isolation:** OS sandbox choices per Linux/Windows/macOS, native extension host model and worker credentials.
9. **Background execution:** per-user versus optional system service, startup, Linux session handling, multi-user and lock-screen notifications.
10. **Extension SDK:** Wasm Component Model and/or IPC JSON-RPC, API compatibility policy, community review governance, funding and hosting.
11. **AI model constraints:** local or remote, accepted metadata/permissions, prompt-injection test fixtures, evidence-quality review criteria and costs.
12. **Mail scope:** baseline IMAP/SMTP, JMAP/CalDAV/Sieve roadmaps, interoperability and credential UX.
13. **Source access policies:** public feeds, web scraping rate limits, provenance retention, content licensing and anti-bot limitations.
14. **Accessibility / terminals:** first officially tested terminal emulators, Unicode/emoji widths, Windows ConPTY behavior, screen readers.
15. **Packaging and code signing:** releases, provenance, SBOM and integration with existing Afrowave infrastructure.
16. **Contribution/review:** code-owner rules, proposal process, issue taxonomy, decision authority, responsible vulnerability disclosure.

Do not assume that an early draft means any of these are decided.
