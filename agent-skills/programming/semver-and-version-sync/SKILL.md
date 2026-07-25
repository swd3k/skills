---
name: semver-and-version-sync
description: Keep product version consistent across assembly, UI, installer, updater, and git tags. Use when versions drift, release notes mismatch, or auto-update compares wrong strings.
---

# SemVer and Version Sync

## Single source of truth
Pick one:
- `Directory.Build.props` `<Version>`
- Or tag-only (CI injects) — then local dev shows `0.0.0-dev`

## Surfaces that must match
- Assembly / InformationalVersion
- UI footer ("v2.0.2")
- Inno `MyAppVersion`
- Updater comparison baseline
- Git tag `vMAJOR.MINOR.PATCH`
- CHANGELOG section header

## Release workflow
1. Bump version in props
2. Update CHANGELOG
3. Commit `release: X.Y.Z — short reason`
4. Tag `vX.Y.Z` and push tags
5. Verify Release assets sizes and notes

## Pitfalls
- UI hardcodes 2.0.2 while props still 2.0.1
- Tag on wrong commit after amend/rebase
- Prerelease tags without clear channel

## Acceptance
- Grep for old version finds nothing relevant
- Updater considers equal versions "up to date"
