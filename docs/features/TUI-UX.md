# Terminal UX, tabs, menus, panels and progress

**Status:** interaction design notes; layouts are illustrative.

## Navigator shell

Full-screen terminal application, keyboard-first but mouse-aware, with address/search bar, tab strip, back/forward/reload, bookmarks, history, menus, rich property panels and configurable theme. Evoke the legibility of classic 1990s Navigator UI without copying protected visual identity/logos; create a distinct Textscape 'T' brand. `F11` page-focused mode; `F12` full developer tools. URL entry and tab operations should work without mastering CLI syntax.

Tabbed views may be web pages, Textbird mail, Workloads, Watchers, FactCheck, AI Work, Data Manager or settings. Tab title badges reflect durable new/unread counts (e.g. `News (2)`, `Textbird (3)`); opening a tab does not implicitly mark all items read. Work can continue after closing a tab; closing a tab and stopping a workload are different actions.

## Activity Indicators with pulldown

Next to URL bar, present icon+total count for cookie events, storage, requests, security and permissions where useful. On mouse hover or keyboard focus, unfold a concise pulldown with allowed/blocked/modified/deleted breakdown. Clicking the main icon opens full detail; clicking a summary category opens the same view filtered to that category. Counts must have documented units and time window; don't conflate current stored items with event counts. Hover must remain open when pointer enters popup; fully keyboard operable.

Emoji where reliable; fall back to monochrome Unicode and ASCII labels when terminals cannot reliably render their width/glyphs. No feature disparity across display modes. Support screen reader semantics as realistically available for terminal UI.

## Progress/status

Classic browser-like loading status line (Off/Compact/Detailed). Honest resource count, request phase, progress with indeterminate fallback where total unknown. Optional inverted monochrome filled bar with correctly inverted characters. Information service is common to mail, downloads, watchers and other tasks. No fake percent. The tab chrome remains visible during SMART-like/long-status updates; UI layout must prevent overlays and clipping.

## Shell panel

Optional bottom split with user-adjustable height, mouse/keyboard resize, collapse/expand, and own PTY/ConPTY session. Launch a *new instance* of the caller's shell where identifiable (Bash, CMD, PowerShell); it is not the blocked parent process and cannot magically inherit mutable runtime state. OS command execution is a manual human activity, not an agent permission. Clipboard bridge may use the separate Rust `ToClipboardTool` design; support terminal OSC52 as optional SSH-safe clipboard adapter only with explicit capability and user policy.

## F12 inspection

Resizable horizontal or vertical split with live page intact: DOM, computed styles, console, network, storage, performance, terminal cell mapping, security activities and raw diagnostics. Export/copy reviewed report. Native UI test harness should cover small terminals, keyboard focus, unicode widths, mouse hover, live badges, large lists and accessible fallbacks.
