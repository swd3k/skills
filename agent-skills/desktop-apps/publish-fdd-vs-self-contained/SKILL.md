---
name: publish-fdd-vs-self-contained
description: Choose and implement .NET publish modes: framework-dependent vs self-contained, single-file, RID graphs. Use when installer size, runtime dependencies, or multi-arch publish is confusing.
---

# Publish: FDD vs Self-Contained

## Decision
| Mode | Size | Needs runtime | Use when |
|------|------|---------------|----------|
| Framework-dependent (FDD) | ~2–10 MB | .NET Desktop Runtime | Default for utilities |
| Self-contained | ~40–80 MB | No | Offline / locked-down PCs |
| Single-file SC | similar | No | One-exe distribution |

## Commands
```powershell
# FDD win-x64
dotnet publish -c Release -r win-x64 --self-contained false

# Self-contained
dotnet publish -c Release -r win-x64 --self-contained true
```

## Multi-arch release set
Ship: `win-x64`, `win-x86` (if needed), `win-arm64` as separate zips/setups.
Document runtime link in README:
https://dotnet.microsoft.com/download/dotnet/8.0

## Pitfalls
- Tagging release "portable 3MB" while CI still builds SC
- Mixing RID folders in one Setup without `[Files]` filters
- Forgetting WebView2 Runtime note for Photino apps

## Acceptance
- Release notes list exact artifact sizes
- Fresh VM install path documented end-to-end
