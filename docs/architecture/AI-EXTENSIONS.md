# AI services, prompt plugins and community catalog

**Status:** proposal. No agent or marketplace integration is implemented.

## AI is optional, not the core dependency

News aggregation, release watching, notifications, mail protocols and most deterministic filtering work without a language model. AI adds analysis, translation, natural-language configuration and summarization where useful. Choose user-approved provider: local/remote Ollama or another model/agent backend through an adapter; display data destinations and capability use. Internal agent/service calls can use MCP where appropriate, not kernel-level hooks.

## Prompt plugins are actual extensions

A prompt pack is a versioned plugin with a visible source text, license, metadata, input slots, model compatibility, expected output schema, tool/data permission request, tests, and optional Rules Engine triggers. Built-in templates are inspectable; the user can clone/edit them without updates overwriting local edits. Community prompts cannot elevate their permissions by changing instructions.

Suggested starter packs: phishing/link inspection, fact check, identify manipulation/neutral rewrite, summarize a page, translate content, review GitHub release notes, summarize GitHub Actions notification, explain a technical document, prepare draft mail (never send without permission), propose diagnostic shell commands (display for *human* execution).

Possible templated slots: `{CurrentURL}`, `{SelectedURL}`, `{SelectedText}`, `{PageContent}`, `{MailContent}`, `{OperatingSystem}`. Values must be explicitly selected according to privacy policy and context; URLs may carry secrets. Placeholder escape/validation and prompt versioning matter. A user may create custom parameters and prompts through a wizard rather than writing files.

## Plugin catalog and publishing

Unify code plugins, source connectors, prompt packs, watcher packs, workflow definitions and themes under a discoverable catalog. Distinguish executable/native modules from data-only prompt definitions. Source inspectable from within Textscape. Proposed review pipeline: author submission -> license/schema validation -> capabilities audit -> injection/adversarial tests -> model compatibility tests -> human/rule-based review -> versioned public listing. Updates are separately reviewed; altered permissions require explicit owner approval.

A manifest is a *request* for permissions, not authorization. Plugin storage uses registered, inspectable providers; non-sandboxed native executables cannot be honestly promised the same comprehensive containment as WASM/process-isolated modules. Consider WIT/WASM Component Model or JSON-RPC IPC for extension APIs, with bounded capabilities and stable schemas.

## AI task boundaries

- No arbitrary agent-run shell, no access to raw authentication tokens, no bypassing browser permission checks.
- AI-generated terminal command is shown to the user; user runs it explicitly in a separate shell. A `ToClipboardTool`-like clipboard workflow can pass outputs back through reviewed clipboard content without direct execution authority.
- Durable AI Work queues/transactional draft revisions; human approval for consequential actions. User can inspect exact prompt version, supplied context and tool events. Traces of tools/evidence are inspectable; do not promise hidden internal model reasoning.
- Optional agent-assisted bug repair occurs in dedicated worktrees/containers with tests, review and pull request; never automatic production code replacement.

## Development automation

Goose is a promising external Rust-based coding agent for the development workflow, not a runtime dependency. Keep instructions in `AGENTS.md` and eventual project configuration. Sequential shared-contract work; independent analysis/tests can be parallel. Every agent change needs independent verification and complete diff review.
