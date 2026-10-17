# Textscape

> **INITIAL CONCEPT — EARLY DESIGN DRAFT (2026-10-17)**  
> **Status:** Architecture and product discovery only. No browser engine, UI, mail service, worker, or plugin runtime has been implemented or validated. All APIs, names, diagrams, and examples are provisional.

**The Web. No Desktop Required.**

Textscape is a proposed open, terminal-native browser and information workspace. The goal is to bring capable web navigation, a built-in email client (**Textbird**), personal automation, event monitoring, optional AI assistance, and unusually transparent privacy controls to the terminal—without requiring a graphical desktop.

Textscape is intended to work across modern desktops, servers, SSH sessions, and constrained hardware. A small device may perform work more slowly or lazily, but features must not be arbitrarily removed based solely on a preselected hardware class. Some platform capabilities (images, audio, desktop notifications, clipboard) necessarily depend on the host terminal or OS.

## The central principles

1. **Glass House:** nothing involving user data or application behavior should be hidden from the owner. Inspect, export, edit where meaningful, delete, and audit supported local data and activities.
2. **User sovereignty:** a web page, plugin, AI model, or vendor cannot overrule user-set browser protections. AI and plugins are separate, constrained security principals; the person using the computer is not an AI agent.
3. **Standards before shortcuts:** reuse well-maintained, legally maintainable open-source components; build a standards-oriented Web platform rather than an imitation or site-specific browser.
4. **Evidence before verdicts:** explain exactly what is claimed, independently supported, unverified, contradicted, or interpreted; preserve exact words when facts warrant them, not euphemisms.
5. **Tests before implementation:** map specification requirements to executable tests; a new engine adapter receives a meaningful, comparable conformance report.
6. **Modular and replaceable:** shared contracts for JS engines, storage, notifications, plugins, AI providers, collectors, and UI frontends.
7. **Slow is smooth:** establish contracts and test baselines sequentially; parallelize only demonstrably independent work.
8. **Localization from the start:** all user-facing strings are localization resources, not hard-coded English UI text.

## Product areas

| Area | Proposed role |
| --- | --- |
| Navigator | Tabbed TUI browser with HTML/DOM/CSS/JS/WASM ambitions, navigation, bookmarks, history and F12 tools |
| Textbird | Email through IMAP/SMTP/MIME, optional JMAP, rules, AI-assisted drafts and notifications |
| Workloads | Durable, repeatable data collection and processing pipelines; e.g. one-page personalized news |
| Watchers | Observe future conditions: new releases, authors' articles, edited pages, monitored events |
| Background Worker | Optional separate scheduler that prepares results even when the Navigator UI is closed |
| FactCheck & Language Inspector | Claim-by-claim evidence checking, source lineage, chronological analysis, neutral rewriting |
| Extension Platform | Versioned code, connector, prompt-pack, watcher and workflow plugins |
| Glass House / Data Manager | Inspectable cookies, Web Storage, IndexedDB, cache, permissions, data operations and audit trails |
| Notification Service | Tab counters, terminal bell, OS notifications, sounds, grouping, privacy settings |
| Shell Panel | Optional independent PTY/ConPTY shell session at the bottom of the TUI, controlled by the user |

## Documentation index

- [Vision, scope and product principles](docs/VISION.md)
- [System architecture](docs/architecture/SYSTEM.md)
- [Browser and runtime adapters](docs/architecture/BROWSER-RUNTIME.md)
- [Workloads, watchers and background worker](docs/architecture/WORKLOADS.md)
- [Textbird and notification service](docs/architecture/MAIL-NOTIFICATIONS.md)
- [Glass House, data and privacy](docs/security/GLASS-HOUSE.md)
- [Security and trust boundaries](docs/security/THREAT-MODEL.md)
- [AI, prompts, plugins and community catalog](docs/architecture/AI-EXTENSIONS.md)
- [FactCheck and neutral language](docs/features/FACTCHECK-LANGUAGE.md)
- [TUI/UX interaction model](docs/features/TUI-UX.md)
- [Conformance and regression testing](docs/testing/TEST-STRATEGY.md)
- [API sketches and examples](docs/interfaces/CONTRACTS.md)
- [Localization and accessibility](docs/features/LOCALIZATION.md)
- [Implementation roadmap](docs/planning/ROADMAP.md)
- [Open questions](docs/planning/OPEN-QUESTIONS.md)
- [Publishing this draft to GitHub](docs/planning/PUBLISHING.md)
- [Architecture decision log](docs/decisions/README.md)
- [Contributing](CONTRIBUTING.md) and [AI development guidance](AGENTS.md)

## Status and expectations

This repository is a **design notebook and prospective project seed**, not a functioning application, a released product, a verified security solution, or an endorsement of any specific engine. Conformance, performance, compatibility, AI analysis, and privacy guarantees are targets to test, not claims of existing achievement. Configuration snippets in this repository are illustrative and not stable schemas.

**Licensing:** public visibility does not, by itself, grant reuse rights. The project license and treatment of third-party dependencies remain an explicit decision; see [open questions](docs/planning/OPEN-QUESTIONS.md). No license is silently asserted for code that does not yet exist.
