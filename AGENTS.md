# Boojy Suite — shared working rules

Process and conventions shared by **all** Boojy repos. Applies to every repo under
`~/Documents/Projects/boojy/` — read this alongside the repo's own `AGENTS.md`.

- **Strategy / "why"** (product lineup, roadmap, principles, licensing) → `VISION.md`, not here.
- **App-specific architecture, stack, gates, gotchas** → that repo's own `AGENTS.md` +
  `.claude/rules/`.
- **This file** = the conventions that were being re-stated in every repo. One home each.

## Memory & docs model

The dividing line: **committed + must-follow → a file; incidental + probabilistic → agent memory.**
A critical rule must never live *only* in agent memory.

- **`AGENTS.md`** (this file + each repo's) — always-true rules. Read every session.
- **`.claude/rules/*.md`** — per-area gotchas + durable facts, one topic per file.
- **`dreams.md`** — the current engineering target + its milestone checklist (`- [ ]`/`- [x]`).
  Volatile *this-week* state only — no backlog, no roadmap, no incident log. Pulled from
  `docs/BACKLOG.md`; safe to wipe each milestone.
- **`docs/`** — `ROADMAP.md` (ordered intentions), `BACKLOG.md` (unscheduled someday),
  `FEATURE_TRACKER.md` (what's built vs not, user-facing apps), `FEATURES.md` (prose tour),
  `ARCHITECTURE.md`; plus `archive/`, `private/` (gitignored), `reviews/` (dated reports).
- **agent memory** — incidental cross-session learnings (Claude Code: auto-memory; see the
  Claude Code section).
- **`git log`** — the history. No session ledger.

## Weekly planning ritual

Suite-wide weekly targets live in the suite root's `SUITE_STATUS.md` ("This Week" — one-line,
app-prefixed, disposable; regenerated snapshot via `scripts/suite-status.sh`). The ritual: Sunday,
review the past week together (the agent brings the git facts, Tyr the judgment), then co-draft
next week's list. Don't run it unprompted — the ritual needs Tyr's input. ⚠️ The file is public —
nothing sensitive goes in it.

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

**One exception:** the suite-umbrella repo's `SUITE_STATUS.md` (a generated/weekly status doc with
no gates behind it) may be committed directly to `main` — typically by the weekly ritual.

**Stacked PRs:** GitHub's "MERGED" badge means *merged into its base*, which for a stacked PR is the
previous PR's branch — **not** master. When PR1 of a stack merges, **delete its branch** so GitHub
retargets the rest of the stack to master; before treating any stacked PR as landed, verify with
`gh pr view N --json baseRefName` + `git merge-base --is-ancestor <merge-sha> origin/master`.
(The v0.6 drum-kit editor sat "merged" but stranded for three releases this way.)

## Context-hygiene gate

When session context crosses ~50%, pause active loops, summarise the current task + files touched,
update `dreams.md`, and compact the conversation. Clear context when switching tasks. Be deliberate
about spawning subagents (each is its own request stream) — long context + subagent fan-out is what
drives cost.

## Keep docs current

A structure/roadmap change updates `AGENTS.md` (+ the relevant `.claude/rules/` file + `README.md`)
in the **same commit**. A release bumps the version + `CHANGELOG.md` (+ `FEATURE_TRACKER.md`).

## Working preferences

- **Commits:** professional messages describing the change. **No "Generated with Claude Code" /
  AI-attribution lines.**
- **Don't auto-start dev servers** (`pnpm dev`, `vite`, foreground `flutter run`) — Tyr runs his own
  localhost.
- **Prefer simple, minimal implementations** first; add complexity only when explicitly asked.
- **No automatic test runs** unless asked — gates run on edit (hook) and in CI.

## Claude Code–specific

Only applies when the agent is Claude Code; other agents can skip this section.

- **Loading:** Claude Code walks up the directory tree and loads this file automatically alongside
  the repo's own. In every repo, `CLAUDE.md` is a symlink to `AGENTS.md`.
- **Agent memory** = Claude Code auto-memory; skim `/memory` after a big refactor.
- **Weekly ritual** = the suite-root `/weekly` skill. If a session starts on Sunday or Monday and
  the `SUITE_STATUS.md` "This Week" heading is from a past week, suggest running `/weekly` — don't
  auto-run it.
- **Context hygiene** = `/compact` at the ~50% gate, `/clear` when switching tasks.
