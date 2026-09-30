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

- **`AGENTS.md`** (this file + each repo's): always-true rules, read every session.
- **`.claude/rules/*.md`**: per-area gotchas, one topic per file.
- **`docs/BACKLOG.md`** (per app): the **one planning file**: priority, known bugs, what's next,
  decisions. Shipped work leaves it for `CHANGELOG.md`. No roadmap, dreams or tracker files.
  Other docs only when they earn their place (`ARCHITECTURE.md`, specs, dated `reviews/` that
  are deleted once triaged). Fewer, shorter docs beat complete ones.
- **Agent memory**: incidental cross-session learnings.
- **`git log`**: the history. No session ledger.

## Changelog workflow

Update `CHANGELOG.md` as you go — entries under a top `## Unreleased` section, categorised
`### Bug Fixes` / `### Features` / `### Improvements`. **Each entry is 1–2 lines saying what the
user sees**; design reasoning goes in BACKLOG decisions or a rules file, not the changelog. On
release, rename `## Unreleased` → `## vX.Y.Z — YYYY-MM-DD` and add a fresh empty `## Unreleased`.
Older releases can be condensed to short highlights that link to the full file at a release tag.

## Release process (skeleton — repo specifics stay local)

1. Bump the version (repo's canonical source — `package.json` / `ui/pubspec.yaml` / etc.).
2. `CHANGELOG.md`: `Unreleased` → `vX.Y.Z` + date.
3. Green the repo's gates.
4. Shipped items leave `docs/BACKLOG.md` **in the same commit** (the changelog now records them).
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

- **Commits and PRs carry AI attribution, for transparency:** a `Co-Authored-By:` trailer naming
  the model (e.g. `Claude Opus 5.5 <noreply@anthropic.com>`) and "🤖 Generated with Claude Code"
  at the end of PR descriptions. Messages describe the change; no competitor product names.
- **Don't auto-start dev servers** (`pnpm dev`, `vite`, foreground `flutter run`): Tyr runs his
  own. Check new UI another way (e.g. a headless render) before handing it over.
- **Prefer simple, minimal implementations**, and when pruning docs or features, lean towards
  cutting: git history keeps what's deleted.
- **Test before handing over:** run the gates and tests scoped to the change locally; the full
  matrix runs in CI.

## Claude Code

Claude Code loads this file automatically alongside the repo's own. In every repo `CLAUDE.md` is
a one-line pointer to `AGENTS.md` (not a symlink). Agent memory is Claude Code auto-memory; the
context gate above means `/compact` at ~50% and `/clear` between tasks.
