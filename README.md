# Boojy Suite

**Creativity without limits.** Boojy is a suite of free, open-source creative apps — a DAW, an image
editor, a note-taking app, with more planned — built so students, hobbyists, and independent creators
aren't priced out of professional software. Free forever (no subscriptions, paywalls, or trials),
GPLv3 and developed in public, privacy-first (no telemetry or ads), cross-platform.

**New here?** This page tells you what exists and where to go. **[`VISION.md`](VISION.md)** explains
*why* Boojy exists and where it's heading. Each app repo's own README covers how to run it.
The live site is **[boojy.org](https://boojy.org)**.

## The apps

| Repo | What it is | Replaces | Status |
|------|------------|----------|--------|
| **[boojy-audio](https://github.com/boojyorg/boojy-audio)** | Cross-platform DAW — multi-track audio/MIDI, mixing, VST3 (Flutter UI + Rust engine) | GarageBand, Logic, Audition | **Alpha — v0.5.4**, v0.6 in progress. Highest priority. |
| **[boojy-design](https://github.com/boojyorg/boojy-design)** | Web image editor — paint, shapes, text, layers | Photoshop, Procreate, Canva | **MVP — v0.4.0** |
| **[boojy-notes](https://github.com/boojyorg/boojy-notes)** | Markdown note-taking, block editor, wikilinks, sync (web + Electron) | Notion, Obsidian | **Alpha — v0.4.0** |
| **[boojy-web](https://github.com/boojyorg/boojy-web)** | Source for [boojy.org](https://boojy.org) (Astro static) | — | **Live** |
| **boojy-cloud** | Supabase backend — powers Notes sync today; free-only, no paid tier | — | **Dormant** (private repo) |

*Status updated on releases; for live week-to-week state see [`SUITE_STATUS.md`](SUITE_STATUS.md)
(auto-refreshed snapshot + the current weekly targets). Each repo's `CHANGELOG.md` is authoritative
if this table trails.*

## How this folder works

This repo is the **suite umbrella** — a thin container for cross-project strategy and shared
conventions. Each app is its own independent git repo nested inside it (gitignored here, tracked in
its own remote). This README is an orientation map, **not** how-to-run-an-app docs.

## Where things live

| Looking for… | Go to |
|--------------|-------|
| **Strategy / why** (lineup, roadmap, principles, licensing) | [`VISION.md`](VISION.md) |
| **Live status & weekly targets** (auto snapshot + This Week) | [`SUITE_STATUS.md`](SUITE_STATUS.md) |
| **Shared rules** every repo inherits (process, branch discipline, memory model) | [`CLAUDE.md`](CLAUDE.md) |
| **Brand** (colors, logos, name & handles) | [`docs/BRAND.md`](docs/BRAND.md) |
| **Dev-system** (how the docs/hooks are shaped + repo setup) | [`docs/DEV_SYSTEM.md`](docs/DEV_SYSTEM.md) |
| **Repo scaffold spec** (what a standard Boojy repo contains) | [`docs/REPO_TEMPLATE.md`](docs/REPO_TEMPLATE.md) |
| **App-specific** architecture, stack, gotchas | that repo's own `CLAUDE.md` + `.claude/rules/` |

Starting a new app (e.g. Boojy Video)? Scaffold its repo from
[`docs/REPO_TEMPLATE.md`](docs/REPO_TEMPLATE.md).
