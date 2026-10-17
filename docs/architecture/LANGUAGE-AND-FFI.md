# Implementation Languages, Native ABI and Ownership

> **Architecture direction approved on 2026-10-17:** Rust-led implementation with a C-compatible ABI where cross-language integration is required, and C/C++ wrappers for existing native engines. No code or integration has been implemented. Library selection and concrete ABI remain subject to prototypes and tests.

## Principle: use each language only where it earns its place

| Language | Preferred responsibility | Boundaries and caveats |
| --- | --- | --- |
| **Rust** | Primary application implementation: Navigator orchestration, Textbird protocol/client logic, terminal UI, worker, scheduler, durable tasks, notifications, privacy/data manager, network orchestration, API contracts, prompt/workload/agent and plugin managers, validation harness | Use established crates after evaluating licensing, maintenance and compatibility; unsafe Rust is restricted and reviewed |
| **C** | Small stable, language-neutral **ABI surface** and necessary C shims for native systems or libraries; exported headers and fixed-layout types for native adapter implementers | A C ABI does **not** imply we must implement the application in C; any C source code is justified case by case |
| **C++** | Thin adapters for third-party C++-native engines/libraries (e.g. V8 or other DOM/layout/JS components if selected); necessary native integration only | No app business logic in C++ by default; confine C++ exceptions, allocation and threading inside well-defined adapters |
| **Other languages** | Future community integrations through versioned process/IPC or WASM component contracts where fit for purpose | They must not gain ambient host rights, nor force the Rust core to depend on their runtime |

This is a **division of responsibilities, not a commitment that all three languages will have source files in Stage 1**. A Rust-only initial proof of concept is entirely valid until a native bridge is needed. Browser/JS backends and their own implementation languages are independent third-party components, with separate licenses.

## Proposed boundaries

```text
                  User-facing Textscape TUI (Rust)
                            |
                  Core commands/services (Rust)
                            |
                Versioned Rust traits / contracts
                   /                      \
        Pure Rust implementation      Native adapter host
                                             |
                                C-compatible ABI contract
                                /                    \
                        C/shim adapter         C++ thin wrapper
                                \                    /
                               Third-party native engine
```

**In-process native adapters are trusted native code** and should not be mistaken for sandboxed WASM plugins. For hostile web content or untrusted native components, evaluate **separate process isolation** and an authenticated IPC protocol. A stable C ABI only solves language interoperability; it does not supply memory safety or sandboxing.

## FFI contract requirements

1. **Versioned handshake and capabilities:** version, sizes, feature availability and failure codes must be declared and validated before calls. No exposing unstable Rust `repr(Rust)` structures or C++ STL types in exported signatures.
2. **Ownership:** every allocated object/handle has an explicit owner, retain/release or close path, and documented lifetime; never free with the wrong allocator. Dynamic libraries may not unload while live handles/callbacks still exist.
3. **Types:** use fixed-width C-compatible types, opaque handles and explicit string/buffer lengths/encodings. Distinguish null, empty, missing, invalid and error values.
4. **Errors and panics:** convert Rust errors to bounded codes/structured diagnostics at the boundary. C++ exceptions must be caught in the C++ wrapper; Rust panic must not cross a non-unwinding C boundary. No unexplained aborts.
5. **Concurrency:** document thread confinement, callback ownership, reentrancy, cancellation, event loop and scheduling requirements. DOM and JS realms may be thread-affine.
6. **Garbage collection / host objects:** support engine-specific rooting/tracing for DOM objects; never assume a JSON serialization layer can safely represent arbitrary JS object identity, closures or live asynchronous callbacks.
7. **Security:** audit unsafe boundaries, load paths, code signing/identity where appropriate, subprocess permissions and origin separation.
8. **Portability:** design and test Linux, Windows and macOS builds plus target CPU architectures; C++ ABI is not assumed stable across toolchains.
9. **Licensing:** every native dependency and transitive dependency is inventoried; no incompatible third-party license is re-licensed by the Textscape policy.

## Candidate module map (conceptual only)

```text
textscape-cli        Rust    terminal executable and session/client
textscape-core       Rust    commands, events, permissions, settings
textscape-tui        Rust    terminal views, focus, tabs, shortcuts
textscape-browser    Rust    browsing/session, resources, adapters
textscape-worker     Rust    scheduler, queues, IPC, background services
textbird             Rust    IMAP/SMTP/MIME client and workflows
textscape-conformance Rust   fixtures, runner, verification reports
textscape-ffi        Rust/C  public native ABI, headers when needed
js-adapter-*         Rust/C/C++ as needed by each selected engine
```

Names and packaging are sketches, **not created crates**.

## Prototype gates before freezing API

- A tiny Rust service works independently of the TUI with deterministic tests.
- A *necessary* native dependency is called through a boundary with tested creation, callback and shutdown.
- Validate malformed inputs, nulls, allocation/deallocation, exception/panic translation, cancellation, threading and process crash behavior.
- At least two interchangeable implementations pass the same interface contract before promising community ABI stability.
- Record measured CPU/RAM/startup overhead and artifact sizes; no unsupported claims that one design is universally fastest.
- Maintain localization from inception; the ABI must carry stable machine-readable error IDs, not hard-coded English messages.

See [system architecture](SYSTEM.md), [browser runtime](BROWSER-RUNTIME.md), [contract sketches](../interfaces/CONTRACTS.md), [test strategy](../testing/TEST-STRATEGY.md), and [ADR 0001](../decisions/0001-rust-first-native-interop.md).
