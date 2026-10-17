# ADR 0001 — Rust-first core with targeted C/C++ interoperability

- **Status:** Accepted in principle (language allocation); implementation/ABI details still proposed
- **Date:** 2026-10-17
- **Related requirements:** TS-CORE-001, TS-JS-001, TS-SEC-001, TS-L10N-001
- **Implementation:** NOT STARTED; test status: NOT_RUN

## Context

Textscape targets Linux, Windows and macOS terminals, constrained systems, an optional background worker, replaceable browser engines and native third-party components. Writing the entire application in C++ would enlarge a traditionally unsafe surface; requiring every dependency to be native Rust would discard mature existing web/JS implementations.

## Decision

**Rust is the default implementation language for Textscape-owned business logic, frontends, background services, data/permission handling and test infrastructure.** Provide a **versioned C-compatible ABI** at the boundary to external native engines when needed. Use **C source only for justified shims** and **C++ only for narrow wrappers/adapters around selected C++ dependencies**. Implementations may remain pure Rust until an interop need is proven.

Keep engine-native types, GC internals, exceptions, allocators and thread rules behind the adapter boundary. Native loading is not a sandbox. Sandbox/process isolation and a future language-neutral plugin SDK are separate design problems.

## Options considered

- **All Rust:** preferable where viable, but limits reuse of some mature native engines.
- **All C++:** broad native compatibility, but not preferred for core safety/maintenance.
- **Rust core + C ABI + thin C++ adapters:** selected for modularity, maintainability and freedom to test/replace browser engines.
- **Everything over JSON-RPC:** insufficient for some synchronous GC/DOM/native interactions; potentially useful at process/plugin boundaries.

## Consequences and validation

- Additional FFI tests and ABI governance; third-party dependency and runtime footprint review.
- Clear allocation, lifetime, panic/exception, thread and callback contracts.
- Core logic must not depend on engine-specific objects.
- No claim of implemented FFI or cross-platform support until actual builds and tests exist.
- Selected engines, binary layout, package graph, ABI 1.0 and process boundaries need separate prototype-backed decisions.

Full language matrix and verification gates: [Implementation languages](../architecture/LANGUAGE-AND-FFI.md).