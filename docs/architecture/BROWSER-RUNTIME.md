# Browser runtime, JS engine adapters and developer tools

**Status:** experimental direction; no selected working engine.

## Requirements

A full-featured TUI browser should support navigation, tabs, history, bookmarks, interactive DOM and modern JavaScript, asynchronous operations, modules and—where a suitable runtime supports it—WebAssembly, including realistic Blazor WASM smoke scenarios. This is not merely a Lynx-style reader. CSS is interpreted faithfully where meaningful, then projected into terminal cells; pixel-perfect visual equivalence with GPU browsers is not promised.

## JavaScript Runtime API

Make JS engines interchangeable behind a project-owned, versioned host contract; extensions can provide new adapters after conformance validation. Candidate logical interfaces:

- `JsEngineFactory` / `JsRuntime` — initialize, configure, tear down.
- `JsRealm` — isolated page context and global objects.
- `JsEvaluation` — scripts, module loading, exceptions.
- `JsValueHandle` — opaque handles; do not expose V8/SpiderMonkey internal types to other modules.
- `JsHostBindings` — DOM and Web API objects with permission and origin handling.
- `JsScheduler` — Promise microtasks, timer integration and event loop semantics.
- `JsDiagnostics` — exceptions, console, evaluator, debugger hooks where available.
- `JsCapabilities` — declared and *tested* supported features including WASM/debugger.

The hard part is cross-runtime object lifetime, rooting and tracing with DOM objects and garbage collectors, promises, module resolution and isolate termination. These cannot be safely reduced to a trivial `eval(string)` interface or naïve JSON serialization. Changing runtime for an active live JS heap is out of scope; allow selection before session start, and verify equivalence across engines.

Adapters may need stable native ABI / isolated processes, not just language-neutral JSON-RPC, especially for synchronous native bindings and GC tracing. Trade-offs require prototypes.

## Conformance

Reuse [Test262](https://github.com/tc39/test262), [Web Platform Tests](https://web-platform-tests.org/), and the [WebAssembly specification suite](https://github.com/WebAssembly/spec) under their actual terms; add project integration tests. Map requirements -> executable test IDs -> results -> failures -> environment/build IDs. Separate unsupported/not-run/fail/timeout/crash/harness error. A manifest is not evidence of passing a feature.

## F12 developer tools

- Inspector: DOM tree, select/edit, attributes, computed styles, layout measurements and terminal renderer cell mapping.
- Console: inspect logs and evaluate JS in the page's JS context, never in the OS shell.
- Network: requests, redirects, headers, payloads, timings, filtering decisions, cache.
- Storage: cookie/Web Storage/IndexedDB/Cache and permissions with exact origin/partition scope.
- Debugger: breakpoints/stepping only if supported by selected engine; never fake capability.
- Diagnostics: complete actionable error reports, related conformance tests, comparison between engines; side-by-side or top/bottom resizable panes without reloading page.
- Secret redaction and per-item user consent for diagnostic exports.

## Initial prototype gates

1. Parse/load a static page and render meaningful text/layout in terminal.
2. Wire a JS runtime into a minimal DOM mutation example.
3. Validate event ordering, module execution, async microtasks, GC roots and shutdown.
4. Add an independent second adapter to prove the contract is actually portable.
5. Reproduce a small unmodified modern JS app, then a WASM/Blazor scenario on supporting engines.

No engine recommendation should be treated as an already-tested selection.
