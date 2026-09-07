---
name: suite-sync
description: Quick mechanical check that suite-root docs (README.md, VISION.md) match each app repo's canonical version. Run after any release, or anytime you suspect version drift. Takes ~30 seconds. Not a full audit.
disable-model-invocation: false
---

# /suite-sync — suite-root version sync check

Quick mechanical check: are the version tables in the suite-root umbrella docs (README.md, VISION.md) up to date with what each app repo actually ships?

## What to check

Read these files in parallel:

**Canonical version sources (ground truth):**
- `~/Documents/Projects/boojy/boojy-audio/ui/pubspec.yaml` — `version:` line (strip the `+build` suffix)
- `~/Documents/Projects/boojy/boojy-notes/package.json` — `"version"` field
- `~/Documents/Projects/boojy/boojy-design/package.json` — `"version"` field

**Suite-root docs to check against:**
- `~/Documents/Projects/boojy/README.md` — apps table (one row per app)
- `~/Documents/Projects/boojy/VISION.md` — product table + competitor table + "Now" roadmap bullet + "Status as of" date

## Checks

For each app (Audio, Notes, Design):
1. Extract the canonical version from the source file
2. Find every reference to that app's version in README.md and VISION.md
3. Report: ✓ matches / ✗ stale (show what the doc says vs what the source says)

Also check:
- VISION.md "Status as of" date — is it more than a week old?

## Output format

Lead with a one-line verdict: **All in sync** or **X items out of sync**.

Then a compact table:

| Doc | App | Doc says | Should be | Status |
|-----|-----|----------|-----------|--------|
| README.md | Audio | v0.5.4 | v0.6.0 | ✗ stale |
| VISION.md | Notes | v0.4.0 | v0.5.0 | ✗ stale |
| README.md | Design | v0.4.0 | v0.4.0 | ✓ |

Then list any other staleness (VISION.md date).

## If fixes are needed

Ask: "Fix these now?" If yes, apply the targeted edits — version strings only, no surrounding content changes.

Do NOT touch any per-app doc — this skill is suite-root version tables only. Broader doc drift needs a proper review, not this skill.
