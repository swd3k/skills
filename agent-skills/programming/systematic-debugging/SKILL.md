---
name: systematic-debugging
description: Debug software issues with a structured reproduce → isolate → fix → regress loop. Use when facing white screens, flaky CI, production-only bugs, or vague 'it doesn't work' reports.
---

# Systematic Debugging

## Loop
1. **Reproduce** — exact steps, OS, version, artifact (not only source).
2. **Define expected vs actual** in one sentence each.
3. **Bisect** — last known good commit/tag/build.
4. **Isolate layer** — UI / host bridge / service / OS / network / packaging.
5. **Hypothesize one cause** — test cheapest disproof first.
6. **Fix minimal** — no drive-by refactors in the same commit.
7. **Regress** — add a test or checklist item so it can't return silently.

## Evidence > intuition
- Logs with timestamps
- Exit codes
- Network traces
- Screenshots / screen recordings
- `git bisect` when regression window is large

## Desktop-specific
| Symptom | First checks |
|---------|--------------|
| White screen | asset load path, CSS blocked, JS throw |
| Works in VS, fails installed | cwd, relative paths, missing runtime |
| CI only | path case, secrets, runner OS, corrupted downloads |
| Admin only | manifest, UAC cancel path |

## Output when reporting
- Root cause (one paragraph)
- Fix (what changed)
- How verified
- Residual risk

## Pitfalls
- Changing 5 things at once
- "Fixed" without reproduction of original failure
- Ignoring the packaging step (only testing `dotnet run`)
