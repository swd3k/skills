---
name: elevate-privileges-safely
description: Request Windows admin rights only for the operations that need them (hosts file, services, drivers). Use when fixing always-admin manifests, UAC prompts, Defender false positives, or hosts/system file writers.
---

# Elevate Privileges Safely

**Least privilege by default.** Elevate a single operation, not the whole app lifetime.

## Prefer
| Goal | Pattern |
|------|---------|
| Edit hosts | `asInvoker` app → spawn elevated helper once |
| Write Program Files | installer elevates; runtime stays user |
| Service control | separate elevated CLI verb |

## Anti-patterns
- `requireAdministrator` in app.manifest for the whole UI
- `powershell -ExecutionPolicy Bypass -Command ...` for simple file writes
- Storing admin password / auto-elevating loops

## Hosts-file recipe (Windows)
1. App runs as normal user.
2. User clicks Apply.
3. Host prepares temp file with desired content.
4. Launch elevated `cmd` / small helper:
   ```
   copy /Y temp hosts
   ipconfig /flushdns
   ```
5. Return exit code to UI; show success/failure.

## Manifest
```xml
<requestedExecutionLevel level="asInvoker" uiAccess="false" />
```

## Defender / SmartScreen notes
- Unsigned binaries still warn; signing is the real fix
- Reduce heuristics: no encoded PS, no process hollowing patterns, milder packers
- Document why elevation is needed in UI and README

## Acceptance
- Everyday browsing of the app never prompts UAC
- One clear UAC prompt per privileged action
- Failure without admin leaves system unchanged
