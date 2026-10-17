# Vision and non-negotiable principles

**Stage:** initial proposal, 2026-10-17. Nothing in this document represents an implemented feature.

## Purpose

Build a capable standards-oriented web and information workspace for people who value ownership, transparency, automation, portability, and practical longevity. A terminal should not imply a second-class, text-only internet. Browser functionality and web APIs should not be arbitrarily disabled just because output is rendered in cells; some pixel-perfect presentation is inherently approximate.

User-facing interactions must remain friendly to nontechnical users. Common activities should have full menus, discoverable shortcuts, contextual help, clickable details, accessible keyboard navigation, and guided configuration. Advanced users can automate through commands and stable extension contracts without replacing the accessible UI.

## The Glass House commitment

- Expose all browser-managed user data, storage providers, permissions, connections, and background activity to its owner.
- Display exactly which application-level data a report/agent/network operation proposes to send and to whom, **before approval**; then show transmission and processing status. Prepare an immutable reviewed payload and send that same payload; if it changes, review again.
- Track reason and rule behind filtering decisions and meaningful changes. No secret telemetry, stealth uploads, undisclosed AI prompts, or silent policy bypasses.
- Provide inspect, export, targeted edit (where valid), and erase options, plus honest explanations when copies may remain in backups, remote systems, or SSD wear-leveling.
- Permit users to block advertising and tracking, control cookies individually or through rules, and inspect storage contents directly. Avoid breaking sites unnecessarily; make exceptions explicit and local.
- Distinguish owner access from web-page, plugin, and AI-agent access. Human control does not imply a website or model receives the same permissions.

## Evidence-based language

Use the **most precise and strongest wording warranted by available evidence**. No euphemistic softening of established conduct; no unsupported escalation. Apply symmetrical tests to equivalent acts regardless of the identity of the actor. A neutral rewrite is not a legal opinion unless a legal profile is explicitly selected. Attribute opinions, allegations, and estimates to their sources; preserve actor, victim, intent, chronology and consequences when supported.

## Constraints and priorities

- Rust is the current leading host-language proposal, not yet an irrevocable choice.
- Native terminal UI first; optional GUI later only if justified.
- Single app UX, separate replaceable services beneath it.
- No arbitrary feature tiers for 2 GB versus modern machines; schedule work lazily and respect constrained resources.
- Prefer RSS/Atom and official APIs to aggressive scraping; use DOM and optional AI only when necessary.
- Open components must have licenses permitting long-term maintenance/forking; independently review transitive obligations.
- Work should be staged: define expected behavior, build tests, implement a small vertical slice, verify, then expand.

## Explicit non-goals for the first implementation

A home-grown ECMAScript language engine; a new CSS specification; writing an entire email server; an autonomous self-modifying production browser; a built-in censorship or one-click "truth percentage" classifier; every planned plugin before a functioning core; an immediate native GUI.
