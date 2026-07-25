---
name: loading-empty-error-states
description: Design loading, empty, and error UI states so the product never feels broken or blank. Use when users report white screens, silent failures, or unclear progress.
---

# Loading · Empty · Error

Every async view needs **three states** besides success.

## Loading
- Skeleton or spinner **with label** ("Checking hosts…")
- Prefer skeletons for content-shaped layouts
- Timeout → error with retry

## Empty
- Explain what will appear and how to start
- One clear CTA
- Not a blank white panel

## Error
- What failed (human language)
- What to do (Retry, Open docs, Run as admin…)
- Keep previous good data if partial

## White screen is a bug
Treat pure white/blank as highest severity:
1. Is CSS loaded?
2. Is root mounted?
3. Did JS throw?
4. Is webview still navigating?

## Acceptance
- No path leaves the user with zero chrome and zero message
