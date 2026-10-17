# Glass House: data ownership, visibility and privacy controls

**Status:** binding design intention, not a claim of implemented enforcement.

## Owner-first behavior

The person who operates the computer is the ultimate owner of local Textscape-managed data and settings. The site, plugin, remote provider and AI agent do not inherit owner privileges. No invisible analytics/telemetry or automatic diagnostics upload. Anything sent externally should be explained and disclosed; privileged data paths require user authorization.

## Data Manager

Expose inventories and editing/export/removal for:

| Provider | Visibility and operations |
| --- | --- |
| Cookies | Name, **actual** value with intentional reveal control, domain/path, expiry, Secure, HttpOnly, SameSite, Partitioned attributes, source, creation/use events and policy outcomes. Inspect, selectively edit when valid, export, delete, block. |
| LocalStorage | All origin keys/values, formats (plain text/JSON/other), sizes, edit, import/export, delete. |
| SessionStorage | Same, scoped correctly to page/tab/session. |
| IndexedDB | Databases, object stores, indexes, records, structured-clone values, binary previews, safe edit/export/deletion. |
| Cache API / HTTP cache | Stored requests/responses or cached objects, sizes, ownership, inspect/export/remove where technically available. |
| Service Workers | Registrations, scope, lifecycle, cache and unregister controls. |
| Permissions | Per-site grants, revocation, scope and when granted. |
| History and downloads | Search/filter/export/remove, plus clear disclosure of external downloaded file handling. |
| Textbird, agent tasks, plugins | Managed data inventory, policy, per-provider audit and clear-data operations subject to owner privileges. |

Account for origin, storage partition, profile, site, and tab scoping—not just hostnames. Viewing protected cookie values in a privileged owner UI **does not make them available to page JavaScript**. Treat exported data as potentially containing secrets.

## Privacy and content policy

Policy should be enforceable at network/request, cookie receive/send, JS storage bindings and other meaningful egress surfaces. Support network filtering, cosmetic filtering, local rule lists and exceptions, first/third-party and partition decisions, per-cookie actions, permissions, rule explainability. Consider uBlock-compatible filter lists after compatibility/license analysis. Do not automatically label every unknown cookie as a tracker; do not blindly accept everything either. Default profile must balance site compatibility with user control; always show why blocked/allowed. Site cannot silently disable the user's policy; if a site breaks, show rule-level diagnostics and limited temporary exceptions.

The live address-bar **Activity Indicator** shows a single overall count (whose semantics are clearly labeled, e.g. cookie events in this session), with hover/focus pulldown breaking down allowed/blocked/modified/deleted and click/keyboard navigation to full detail. Do not conflate stored-cookie count with events. Equivalent views apply to storage/network/security/permissions.

## Diagnostics submission

Create an immutable payload of exactly the application-level data intended for transmission. Automatically display the complete reviewable payload and its destination **without requiring a "show details" action**; user must authorize any external report. For attachments show type, size, hash and inspect/export options, and show actual content when inspectable. After sending, display real transport/processing events and replies. Any material change requires a fresh approval. No promise of recalling already-delivered data. Distinguish application payload from TLS/network transport internals.

## Deletion and limits

The owner can delete local managed data with clear irreversible choices; no secretly retained shadow copies. Disclose backups, synced remote data and media constraints: physical secure erasure of individual SSD blocks may not be verifiable. Agents are separately constrained from permanent deletion. Transactional integrity and explicit cleanup after plugin uninstall are important.

## Mandatory acceptance tests

Enumerate every record a provider claims to manage; create/read/export/edit/delete cookies, local storage and IndexedDB; test HttpOnly against page JS; monitor allowed/blocked network actions; validate no payload drift after approval; confirm all plugin-managed data are discoverable; no hidden telemetry; no status count deception; restart and verify persisted settings/deletion outcomes.
