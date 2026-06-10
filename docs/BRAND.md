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
