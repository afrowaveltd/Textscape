# Proposed system architecture

**Status:** design hypothesis. Module names and APIs are provisional.

```text
+------------------ User-facing Frontends -------------------+
| TUI Navigator (tabs, menus, URL, status, F12, shell panel) |
| Textbird views | Workload views | Data Manager | FactCheck |
+-------------------------------+---------------------------+
                                | Command / View APIs
+-------------------------------v---------------------------+
| Core services                                             |
| Browser Session / Navigation / URL / Resource Pipeline     |
| Events | Commands | Scheduler | Rules | Durable Tasks      |
| Permissions/Capabilities | Privacy Policy | Storage       |
| Notification Service | Audit / Diagnostics / Progress     |
+-----------------------+-------------------+---------------+
                        |                   |
+-----------------------v------+ +----------v-------------+
| Browser backend & adapters | | Extension / AI Gateway    |
| HTML, DOM, CSS, JS, WASM    | | Connectors, prompt packs  |
| Terminal renderer adapter  | | Model/provider adapters   |
+------------------------------+ +------------------------+
                        |
+-----------------------v-----------------------------------+
| Optional independent per-user Textscape Worker            |
| Scheduled fetch, mail sync, watchers, analysis, events     |
+-----------------------------------------------------------+
```

## Independence and boundaries

- UI is a consumer of services; closing a workload's tab must not cancel its durable work by accident.
- A `BrowserSession` provides navigation, resource/session state and front-end-facing operations. A future GUI could reuse those contracts while owning a different platform WebView DOM/JS implementation; no promise of sharing a live heap between unrelated engines.
- A single logical scheduler and durable task ownership protocol prevents duplicate work when a worker and UI coexist. Lease/heartbeat, idempotence keys, retries, and transactional state are mandatory design requirements.
- Event Bus communicates state changes; Notification Service turns them into badge counts, alerts, sound, OS delivery. Badges are derived from durable read/unread/new status, not from ephemeral tab counters.
- AI agents and plugins are distinct authenticated principals with scoped capabilities, auditing, and no ambient access to OS credentials, shell, or internal data.
- Commands are uniform and drive TUI menus, shortcuts, optional CLI, plugin actions, and future GUI, with a stable versioning strategy.

## Implementation language allocation

**Accepted architecture direction:** Textscape-owned core, TUI, mail, worker, storage, privacy, automation and tests are written primarily in **Rust**. A **C-compatible ABI** is the stable cross-language boundary when a native engine is integrated; dedicated **C shims** and **thin C++ wrappers** are used only where necessary. Native FFI is not a security boundary; process isolation must be considered separately. No concrete ABI, C/C++ adapter or Rust code has been implemented. See [language and FFI architecture](LANGUAGE-AND-FFI.md) and [ADR 0001](../decisions/0001-rust-first-native-interop.md).

## Candidate components (not commitments)

- Rust workspace as agreed default; `ratatui`/`crossterm` for TUI are candidate dependencies, with native terminal images where available.
- DOM/layout choices to prototype rather than presume (Servo research candidate, potentially an independent adapter); JS candidates QuickJS-NG, Boa, SpiderMonkey and V8.
- Native process isolation where possible for hostile content and risky native adapters; per-process memory/CPU constraints.
- SQLite or comparable durable local store, with schema migration, transactional updates and backup/export; final technology undecided.
- Unix socket / Windows Named Pipe for authenticated IPC between UI and worker; desktop-specific notification adapters.

## Integrations

- Textbird IMAP/SMTP/MIME; optional JMAP, calendars, contacts and rule processing.
- Watchers/collectors: RSS/Atom, GitHub Releases/API, GitLab, public APIs, web DOM, community connectors.
- AI provider adapters for local/remote systems (e.g. Ollama); MCP at user-space service boundary.
- Optional OS shell panel: separate instance of the launch shell via PTY (Unix) or ConPTY (Windows); it cannot be the waiting parent shell instance. No automatic agent shell execution. Use explicit copy/paste or user-authorized workflows.

## Long-lived contracts

Document contracts before implementation; avoid accidental leaks of engine-specific types into core APIs. Every capability should declare its permissions, lifecycle, availability, versions and test coverage. For a narrow first milestone implement only a vertical slice, not a generic abstraction for every conceivable future system.
