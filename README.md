# Boojy Suite

**Creativity without limits.** Boojy is a suite of creative tools that are *free forever* (no
subscriptions, paywalls, or trials), open-source after each app reaches v1.0, privacy-first (no
telemetry or ads by default), and cross-platform — built so students, hobbyists, and independent
creators aren't priced out of professional software. The full strategy, principles, and product
rationale live in **[Boojy Suite — Vision (2026 Refresh)](<Boojy Suite — Vision (2026 Refresh).md>)**.

> This folder is the **suite umbrella** — a thin container for cross-project strategy and shared
> conventions. Each app is its own independent git repo nested inside it (and gitignored here, so it's
> tracked only in its own remote). This README is an orientation map, **not** how-to-run-an-app docs —
> each repo's own `README.md` covers that.

## The repos

Live versions and per-app status are generated into **`~/Documents/Vault/Boojy/SUITE_STATUS.md`**
(via `boojy-web/scripts/suite-status.sh`) — that's the canonical, non-drifting status source.

| Repo | What it is | Maturity |
|------|------------|----------|
| **boojy-audio** | Cross-platform DAW (Flutter UI + Rust engine over FFI) | Active |
| **boojy-design** | Web image editor (the "Classic" layout: top bar, tool rail, canvas, sidebar) | Active |
| **boojy-notes** | Markdown-based note-taking app for web (PWA) + desktop (Electron) | Active |
| **boojy-web** | Source for [boojy.org](https://boojy.org) — the marketing site (Astro static) | Live |
| **boojy-cloud** | Supabase backend (auth, sync, attachments) — deferred until the apps ship | Not active |

## Where things live

| Looking for… | Go to |
|--------------|-------|
| **Strategy / why** (lineup, roadmap, principles, licensing) | [Vision doc](<Boojy Suite — Vision (2026 Refresh).md>) |
| **Shared rules** every repo inherits (process, branch discipline, memory model) | [`CLAUDE.md`](CLAUDE.md) |
| **Dev-system** (how the docs/hooks are shaped + how to set up a repo) | [`DEV_SYSTEM.md`](DEV_SYSTEM.md) |
| **What a standard Boojy repo contains** (scaffold spec for a new app) | [`REPO_TEMPLATE.md`](REPO_TEMPLATE.md) |
| **Brand** (colours, logos, naming) | [`Boojy Colors.md`](<Boojy Colors.md>) · [`Boojy Logos.md`](<Boojy Logos.md>) · [`Boojy name.md`](<Boojy name.md>) |
| **Live status / versions** | vault `SUITE_STATUS.md` (generated) |
| **App-specific** architecture, stack, gotchas | that repo's own `CLAUDE.md` + `.claude/rules/` |

Starting a new app (e.g. Boojy Video)? Scaffold its repo from **[`REPO_TEMPLATE.md`](REPO_TEMPLATE.md)**.
