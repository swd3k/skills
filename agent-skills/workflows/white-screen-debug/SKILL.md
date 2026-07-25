---
name: white-screen-debug
description: Diagnose blank/white UI in web and desktop webview apps with a ordered checklist. Use when the window opens empty, CSS fails, or only HTML shell shows.
---

# White Screen Debug

## Ordered checks
1. **Process alive?** window opened, no crash loop
2. **URL / load method** — file://, https://, data, LoadRawString
3. **DevTools console** — first exception wins
4. **Network/assets** — CSS/JS 404 or blocked
5. **Path packing** — works in dev, fails in publish (cwd, case, asar)
6. **WebView2 / browser runtime** installed?
7. **CSP** blocking inline or file scripts?
8. **Theme** — white text on white? (not true white screen but looks empty)

## Photino-specific
- file:// primary for multi-file UI
- raw string requires inlined CSS
- Log absolute path passed to Load

## Fix pattern
- Minimal repro HTML (red body background) to prove paint works
- Then reintroduce CSS/JS layers

## Acceptance
- Root cause named; regression note added
