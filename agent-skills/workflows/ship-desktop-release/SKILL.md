---
name: ship-desktop-release
description: End-to-end checklist to ship a desktop app GitHub release: version sync, changelog, installers, CI, notes, post-verify. Use when cutting vX.Y.Z for Windows tools.
---

# Ship Desktop Release

## Checklist
1. [ ] Version bumped everywhere (props, UI, installer, updater)
2. [ ] CHANGELOG section written (user-facing)
3. [ ] Tests green locally
4. [ ] Installers built (correct FDD/SC mode)
5. [ ] Smoke install on clean-ish machine
6. [ ] Tag `vX.Y.Z` on the intended commit
7. [ ] CI release green **or** manual assets uploaded complete
8. [ ] Release notes formatted; artifacts named clearly
9. [ ] SHA256 published if you claim checksums
10. [ ] README links still correct

## After ship
- Install from Release URL (not local bin)
- Run update path from previous version if applicable
- Watch first issues 24h

## Pitfalls
- Tag on old commit after force-push
- Partial asset upload ("someone will add later")
- CI workflow on tag still old/broken
