# Boojy Brand

One home for the decided brand facts: colors, logo conventions, and the name/handles. For colors,
the **production source of truth is `boojy-web/website/src/styles/shared.css`** — this doc
summarises; the CSS decides. (Early palette/logo ideation lives locally in `archive/brand/`, not
here — this file records decisions, not options.)

## Colors

| Use | Value | Notes |
|-----|-------|-------|
| Site accent | `#7C8CFF` (rgb 124 140 255) | Periwinkle blue, chosen 2026-06-01 (was gold) |
| Boojy Notes | `#A4CACE` | Soft teal |
| Boojy Audio | `#4A9EF5` | Blue |
| Boojy Design | `#FFA500` | Orange (matches the Design wordmark badge `#E89940`) |
| Boojy Video | — | Unassigned — app not started |

*(White was Boojy Cloud's colour; retired with the 2026-08 Cloud drop, free for reuse.)*

## Logos

- **Web asset convention:** lowercase `<app>-text-logo.png` (e.g. `audio-text-logo.png`), in
  `boojy-web/website/public/images/`, sized by **height** in CSS so widths vary per wordmark.
- ⚠️ Renames that only change case (e.g. `Notes-Text-Logo.png` → `notes-text-logo.png`) look fine on
  macOS but break on the Linux build — rename in two steps or via `git mv`.
- Suite mark: `boojy-logo.svg` / `Boojy_Image_Logo.png` (favicon derives from these).

## Suite continuity (decided 2026-08-24)

The apps should feel like siblings — same icons, same design language, shared components where the
stacks allow. Decided facts:

- **Icons: Lucide, everywhere.** `lucide-react` on the web (Notes and Design already use it;
  boojy-web inlines Lucide paths); the Lucide Flutter package in Audio. No second icon family, no
  one-off glyphs where a Lucide icon exists.
- **Reference implementation: Boojy Design.** Its component setup (Radix primitives + Tailwind +
  CVA, documented in Storybook) is the pattern the other web surfaces adopt — Design is where a
  shared convention lands first, then Notes and boojy-web follow. A shared component package for
  the three React surfaces is the eventual goal; until it exists, copy the Design pattern rather
  than inventing a parallel one.
- **Audio mirrors, it doesn't import.** Flutter can't consume the React components, so Audio
  matches the tokens, spacing, and interaction grammar by hand. Parity of feel, not of code.
- **Tone: hobbyist.** Approachable and calm (GarageBand-level, per `VISION.md`), quiet motion,
  no dense pro-tool chrome.

## Top bar / app chrome (the suite contract)

Every app's top bar follows the same grammar:

- **The app logo (top-left) opens the app menu** — app-level actions (settings, about, quit).
- **The project/document name (top-centre) opens the document menu** — file-level actions
  (rename, save/export, recent files).

Boojy Design is the reference implementation (tracked in its backlog); Audio and Notes retrofit
once the pattern is proven there.

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
