---
name: github-autoupdate-desktop
description: Ship in-app updates from GitHub Releases for desktop apps (.NET, Electron, Tauri). Use when implementing version checks, silent installers, or update UX.
---

# GitHub Releases Auto-Update (Desktop)

## Flow
1. On launch (or daily): `GET /repos/{owner}/{repo}/releases/latest`
2. Compare SemVer with local `AssemblyInformationalVersion` / package version
3. If newer: show release notes summary + Download & Install
4. Download asset matching RID/channel
5. Verify SHA256 when provided
6. Run installer elevated if needed; exit app for replace

## User-Agent
GitHub may throttle anonymous calls. Send a descriptive UA:
```
MyApp/1.2.3 (+https://github.com/owner/repo)
```

## UX
- Never force update mid-critical-work without prompt
- Offline: fail quiet with retry later
- Beta channel optional via prerelease flag

## Security
- Prefer HTTPS only
- Prefer signed installers
- Don't execute arbitrary zip contents without path validation

## Pitfalls
- Hardcoding old fallback version that re-triggers loops
- Updating while holding file locks on the exe
- Parsing HTML release pages instead of API

## Acceptance
- Update from N → N+1 succeeds on clean machine
- Already-latest shows "You're up to date"
