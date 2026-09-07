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
- **`docs/BACKLOG.md`** (per-app repos) — the **one planning file**: direction, what's next, known
  issues, someday items, and the decisions behind them. Shipped work leaves it for `CHANGELOG.md`.
  No `dreams.md`, no roadmap file, no feature tracker. Optional alongside it: `ARCHITECTURE.md`,
  `SPEC-*.md` (binding constraints), `archive/`, `private/` (gitignored), `reviews/` (dated
  reports), and a root `FEATURES.md` tour for a user-facing app. *(boojy-audio still carries the
  older `dreams.md` / `ROADMAP` / `FEATURE_TRACKER` shape; it is reorganised when development
  resumes, not before.)*
  The suite-umbrella `docs/` is different — it holds cross-suite references: `BRAND.md`,
  `REPO_TEMPLATE.md`, and `private/` (gitignored).
- **agent memory** — incidental cross-session learnings (Claude Code: auto-memory; see the
  Claude Code section).
- **`git log`** — the history. No session ledger.

## Changelog workflow

Update `CHANGELOG.md` as you go — entries under a top `## Unreleased` section, categorised
`### Bug Fixes` / `### Features` / `### Improvements`. On release, rename `## Unreleased` →
`## vX.Y.Z — YYYY-MM-DD` and add a fresh empty `## Unreleased`.

## Release process (skeleton — repo specifics stay local)

1. Bump the version (repo's canonical source — `package.json` / `ui/pubspec.yaml` / etc.).
2. `CHANGELOG.md`: `Unreleased` → `vX.Y.Z` + date.
3. Green the repo's gates.
4. Shipped items leave `docs/BACKLOG.md` **in the same commit** (the changelog now records them).
   Audio: also tick `docs/FEATURE_TRACKER.md` while it still has that file.
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
note anything that must survive in `docs/BACKLOG.md`, and compact the conversation. Clear context when switching tasks. Be deliberate
about spawning subagents (each is its own request stream) — long context + subagent fan-out is what
drives cost.

## Keep docs current

A structure/roadmap change updates `AGENTS.md` (+ the relevant `.claude/rules/` file + `README.md`)
in the **same commit**. A release bumps the version + `CHANGELOG.md`, and updates the app's row
in the suite root `README.md` (the one cross-suite status; there is no separate status doc).

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
- **Context hygiene** = `/compact` at the ~50% gate, `/clear` when switching tasks.
