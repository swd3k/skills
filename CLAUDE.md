# CLAUDE.md — swd3k/skills

## Purpose

This repository is a **portable library of agent skills** (English `SKILL.md` files) for desktop apps, programming, UI, and web design.

## Before implementing anything in a consumer project

1. Find the **narrowest** matching skill under `agent-skills/`.
2. Read that `SKILL.md` fully.
3. Follow its defaults, workflow, pitfalls, and acceptance checks.
4. Do not invent a parallel process unless the user overrides.

## Authoring new skills

Follow `agent-skills/workflows/agent-skill-authoring/SKILL.md`.

- Frontmatter: `name`, `description` (with clear triggers)
- English body
- No secrets, no private absolute paths
- Keep long essays in `ARTICLE.md`; links only in `REFERENCES.md`

## Categories

| Path | Use for |
|------|---------|
| `desktop-apps/` | Photino, Electron, Tauri, Inno, elevation, tray, updates |
| `programming/` | Architecture, debug, CI, tests, review, versions |
| `ui/` | Product interface systems |
| `web-design/` | Marketing and web craft |
| `workflows/` | Cross-cutting agent loops |

## Style

Match the README tone of other swd3k repos: clear, practical, badge-friendly docs — skill bodies stay procedural English.
