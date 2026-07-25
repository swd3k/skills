---
name: clean-architecture-layers
description: Structure app code into Core, Infrastructure, UI/API layers with clear dependency direction. Use when scaffolding solutions, refactoring god-projects, or deciding where business logic lives.
---

# Clean Architecture Layers

Dependencies point **inward**. UI and frameworks depend on Core — never reverse.

## Default layout (.NET / general)
```
src/
  App.Core/             # domain, use cases, ports (interfaces)
  App.Infrastructure/   # files, HTTP, DB, OS integrations
  App.Ui/ or App.Api/   # Photino, ASP.NET, CLI
tests/
  App.Core.Tests/
  App.Infrastructure.Tests/
```

## Rules
1. Core has **no** UI, EF, Photino, or HTTP client package refs.
2. Infrastructure implements Core interfaces.
3. Composition root (Program.cs) wires implementations.
4. Feature changes: Core first if business rules change.

## Workflow
1. Name the use cases (ApplyHosts, CheckUpdate…).
2. Define ports as interfaces in Core.
3. Implement adapters in Infrastructure.
4. UI only calls use cases / services via interfaces.
5. Unit-test Core without OS; integration-test Infrastructure.

## Pitfalls
- Business rules inside button click handlers
- Circular project references "just this once"
- Huge Shared project that becomes a dump

## Acceptance
- Core tests run on Linux CI without Windows packages
- New storage backend = new Infrastructure class, Core untouched
