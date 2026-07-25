---
name: code-review-pass
description: Review code for correctness, security, UX regressions, and project conventions. Use when reviewing PRs, self-reviewing before push, or auditing agent-generated diffs.
---

# Code Review Pass

## Order
1. Purpose — does the PR solve the stated problem?
2. Correctness — edge cases, nulls, races, elevation
3. Security — injection, path traversal, secrets, IPC
4. UX — error states, loading, destructive confirms
5. Maintainability — naming, layering, tests
6. Ops — CI, version, migrations, rollback

## Must flag
- Secrets or tokens in repo
- Admin elevation widened without need
- Behavior change without tests/notes
- Broken install/update path

## Tone
- Specific file/line references
- Suggest fix, not just "this is wrong"
- Separate blocking vs nit

## Output
- Summary (2–4 sentences)
- Blocking issues
- Non-blocking suggestions
- Testing gaps
