---
name: commit-messages-russian
description: Write clear Russian git commit subjects in conventional style for product repos. Use when committing, rewriting history messages, or enforcing CONTRIBUTING style in Russian projects.
---

# Commit Messages (Russian)

## Format
```
тип: краткое описание
```
Optional body in Russian, neutral tone.

## Types
| Type | Use |
|------|-----|
| `fix` | bug fix |
| `feat` | user-facing feature |
| `docs` | README, notes |
| `ci` | Actions, scripts |
| `chore` | tooling, version bump without feature |
| `refactor` | structure, no behavior change |
| `release` | version cut |

## Good
- `fix: белый экран при LoadRawString`
- `ci: установка Inno Setup из официального релиза`
- `docs: обновленное README`

## Bad
- `update`, `fix stuff`, meme subjects
- Huge subjects that list 12 files
- English/Russian random mix in one subject without need

## Rules
- Subject ≤ ~72 chars
- Imperative / descriptive fact, not essay
- One logical change per commit when practical
