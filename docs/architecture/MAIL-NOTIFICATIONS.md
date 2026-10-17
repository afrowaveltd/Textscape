# Textbird and cross-platform notifications

**Status:** initial architecture.

## Textbird email

Integrate email into Textscape as first-class tabs/views, not as a permanently running browser page. Standards-first IMAP, SMTP and MIME; optional JMAP, ManageSieve/Sieve, CalDAV/iCalendar and contacts via future modules. Multiple accounts and identities, search, folders, drafts, templates, signatures and Markdown editing.

- Produce valid `multipart/alternative` messages with semantically correct plain-text and HTML parts, not an HTML document dumped into text/plain.
- IMAP IDLE when available for near-realtime mailbox updates; compliant polling fallback. JMAP event push when supported by the server.
- Distinguish received/unread/flagged/draft/send-queued/sent statuses and preserve original mail when agents analyze or classify it.
- Vendor-specific provider workarounds belong in optional connectors; generic standards do not assume Outlook/Gmail behavior.

## AI Work for email

Virtual queues over a durable store: `Drafts`, `To Review`, `To Send`, `To Delete`, `Sent`, `History`. They should not silently move original IMAP messages. Agent access requires scoped, revocable permissions. Agents cannot irreversibly delete original mail or gain implicit access to secrets or OS shell. Authorized auto-send rules need explicit policies, loop prevention, idempotency, audit, and clear send state.

AI-authored messages can include configurable public AI signature: global/account/identity defaults, per-rule override, rich/plain-text, or consciously empty. Internal provenance/audit is mandatory regardless of outward signature. Choose relevant `Auto-Submitted` semantics without breaking interoperability.

## Notification Service

Events come from mail, watchers, workloads, agent jobs and security checks into one durable event/notification system. UI and background worker share state; no independent badge counters in each tab.

- Tab `News (2)` indicates new actionable articles, `Textbird (3)` indicates unread mail according to user rules, `Watchers (1)` means an unacknowledged event.
- Visual indicators, grouped notifications, OS notification adapters, sound, terminal BEL and in-app history must be individually configurable.
- Desktop Linux: freedesktop.org Notifications over user D-Bus where available; Windows/macOS native APIs as supported; headless/SSH: visual badge and possibly client terminal bell. A remote BEL plays on the remote terminal only if supported; never assume server audio is useful.
- Desktop notifications may not be deliverable before the user session exists; retain events for later.
- Privacy controls: lock-screen content redaction, do-not-disturb, per-event channel settings, explicit sound opt-in, no audio storm when dozens of items arrive.
- Notification click must open the relevant page, message, watcher or saved result, possibly by starting Navigator.

## Validation

Test duplicate events, concurrent UI windows, interrupted IPC, worker restart, expired notification targets, IMAP reconnect, multiple folders and mail account identities, repeated auto-reply triggers and platform audio fallback.
