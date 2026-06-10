# Boojy Suite — shared working rules

Process and conventions shared by **all** Boojy repos. Inherited by every repo under
`~/Documents/Projects/boojy/` (Claude Code walks up and loads this alongside the repo's own
`CLAUDE.md`).

- **Strategy / "why"** (product lineup, roadmap, principles, licensing) → `VISION.md`, not here.
- **App-specific architecture, stack, gates, gotchas** → that repo's own `CLAUDE.md` +
  `.claude/rules/`.
- **This file** = the conventions that were being re-stated in every repo. One home each.

## Memory & docs model

The dividing line: **committed + must-follow → a file; incidental + probabilistic → auto-memory.**
A critical rule must never live *only* in auto-memory.

- **`CLAUDE.md`** (this file + each repo's) — always-true rules. Read every session.
- **`.claude/rules/*.md`** — per-area gotchas + durable facts, one topic per file.
- **`dreams.md`** — the current engineering target + its milestone checklist (`- [ ]`/`- [x]`).
  Volatile *this-week* state only — no backlog, no roadmap, no incident log. Pulled from
  `docs/BACKLOG.md`; safe to wipe each milestone.
- **`docs/`** — `ROADMAP.md` (ordered intentions), `BACKLOG.md` (unscheduled someday),
  `FEATURE_TRACKER.md` (what's built vs not, user-facing apps), `FEATURES.md` (prose tour),
  `ARCHITECTURE.md`; plus `archive/`, `private/` (gitignored), `reviews/` (dated reports).
- **auto-memory** — incidental cross-session learnings; skim `/memory` after a big refactor.
- **`git log`** — the history. No session ledger.

## Changelog workflow

Update `CHANGELOG.md` as you go — entries under a top `## Unreleased` section, categorised
`### Bug Fixes` / `### Features` / `### Improvements`. On release, rename `## Unreleased` →
`## vX.Y.Z — YYYY-MM-DD` and add a fresh empty `## Unreleased`.

## Release process (skeleton — repo specifics stay local)

1. Bump the version (repo's canonical source — `package.json` / `ui/pubspec.yaml` / etc.).
2. `CHANGELOG.md`: `Unreleased` → `vX.Y.Z` + date.
3. Green the repo's gates.
4. For user-facing apps, tick the shipped items in `docs/FEATURE_TRACKER.md` **in the same commit**.
5. Commit, then tag `vX.Y.Z` and push.

## Branch discipline

Never commit straight to `main`/`master`. Branch → green the repo's gates locally → PR. **CI is the
gate**, not just local tests. Don't bypass pre-commit hooks (`--no-verify`).

**Stacked PRs:** GitHub's "MERGED" badge means *merged into its base*, which for a stacked PR is the
previous PR's branch — **not** master. When PR1 of a stack merges, **delete its branch** so GitHub
retargets the rest of the stack to master; before treating any stacked PR as landed, verify with
`gh pr view N --json baseRefName` + `git merge-base --is-ancestor <merge-sha> origin/master`.
(The v0.6 drum-kit editor sat "merged" but stranded for three releases this way.)

## Context-hygiene gate

When session context crosses ~50%, pause active loops, summarise the current task + files touched,
update `dreams.md`, and `/compact`. `/clear` when switching tasks. Be deliberate about spawning
subagents (each is its own request stream) — long context + subagent fan-out is what drives cost.

## Keep docs current

A structure/roadmap change updates `CLAUDE.md` (+ the relevant `.claude/rules/` file + `README.md`)
in the **same commit**. A release bumps the version + `CHANGELOG.md` (+ `FEATURE_TRACKER.md`).

## Working preferences

- **Commits:** professional messages describing the change. **No "Generated with Claude Code" /
  AI-attribution lines.**
- **Don't auto-start dev servers** (`pnpm dev`, `vite`, foreground `flutter run`) — Tyr runs his own
  localhost.
- **Prefer simple, minimal implementations** first; add complexity only when explicitly asked.
- **No automatic test runs** unless asked — gates run on edit (hook) and in CI.
