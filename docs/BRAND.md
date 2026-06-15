# Boojy Brand

One home for the decided brand facts: colors, logo conventions, and the name/handles. For colors,
the **production source of truth is `boojy-web/website/src/styles/shared.css`** — this doc
summarises; the CSS decides. (Early palette/logo ideation lives locally in `archive/brand/`, not
here — this file records decisions, not options.)

## Colors

| Use | Value | Notes |
|-----|-------|-------|
| Site accent | `#7C8CFF` (rgb 124 140 255) | Periwinkle blue, chosen 2026-06-01 (was gold) |
| Boojy Audio | `#4A9EF5` | Blue |
| Boojy Notes | `#A4CACE` | Soft teal |
| Boojy Design | `#FFA500` | Orange (matches the Design wordmark badge `#E89940`) |
| Boojy Cloud | White | Used for the Cloud status pill |
| Boojy Video | — | Unassigned — app not started |

## Logos

- **Web asset convention:** lowercase `<app>-text-logo.png` (e.g. `audio-text-logo.png`), in
  `boojy-web/website/public/images/`, sized by **height** in CSS so widths vary per wordmark.
- ⚠️ Renames that only change case (e.g. `Notes-Text-Logo.png` → `notes-text-logo.png`) look fine on
  macOS but break on the Linux build — rename in two steps or via `git mv`.
- Suite mark: `boojy-logo.svg` / `Boojy_Image_Logo.png` (favicon derives from these).

## Top bar / app chrome

Every editor app shares one top-bar grammar. Two interactive targets, split by **scope** — the user
never has to guess which to click:

| Target | Position | Click opens | Holds |
|--------|----------|-------------|-------|
| **Logo** (`▲app` wordmark) | top-left | **App menu** (dropdown) | Start screen / All projects · New · Open recent · Preferences · About · Help |
| **Project name** (`Untitled`) | right of logo | **Document menu** (dropdown) | Rename (→ inline edit) · Save · Save As · Save version · Project settings · Export · Close |

Principles:
- **App-level vs. document-level** is the dividing line. App-global actions live under the logo;
  anything scoped to the open document lives under its name.
- ⚠️ **The logo opens a menu — never a bare navigation jump.** "Start screen / All projects" is the
  *first item* in that menu, so a stray click can't throw the user out of their project.
- The project name shows a **dirty dot** (`•`) when there are unsaved changes. Rename happens inline
  (the name flips to an editable field), reached via the document menu — not on a raw click.

Per-app notes:
- **Multi-document apps (Notes)** have no single project-name slot — the tab bar owns document
  switching. They still follow the logo → app-menu rule (Notes' Settings shortcut folds in as
  Preferences).
- Platform chrome (e.g. Audio's macOS title strip showing `Project — Boojy Audio`) is decoration,
  not an interaction target.

Repo-specific implementation gotchas (not the contract) go in each repo's `.claude/rules/top-bar.md`.

## Name & handles (the brand spine)

| Platform | Handle |
|----------|--------|
| Domain | **boojy.org** |
| GitHub | **boojyorg** |
| YouTube | **@boojy** |
| X (Twitter) | **@boojyorg** |
| Instagram | **@boojyorg** |
| TikTok | **@boojyorg** |
| LinkedIn | Company page: **Boojy** |

These were claimed early so the name can't be squatted or impersonated. ⚠️ On GitHub, don't create a
repo named `boojy` under the org — the old `boojy` repo was renamed to `boojy-web`, and a new `boojy`
repo would break GitHub's automatic redirect.
