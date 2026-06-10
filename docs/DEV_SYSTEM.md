# Boojy Dev System — the docs/hooks shape + how to set up a repo

> **How** the suite's docs system is shaped, and the playbook for standing up a new repo in it.
> The always-true *model* — what each file is for, the committed-vs-auto-memory dividing line — lives
> in the suite-root **`CLAUDE.md`**; this file doesn't restate it, it covers **placement + setup**.
> _(Last reshaped 2026-06-03, post-standardisation. Not a line-by-line maintained spec — `git log`
> and auto memory own the living state.)_
>
> Part of the suite-doc set: [`VISION.md`](../VISION.md) (suite root) = **why**
> (strategy); this file = **how** (conventions + setup). Operational status — *SUITE_STATUS.md* — is
> auto-generated into the vault (`~/Documents/Vault/Boojy/SUITE_STATUS.md` via
> `boojy-web/scripts/suite-status.sh`), not here.

---

## Placement rule (repo vs suite root)

Anything a coding agent reads while working *inside* a repo lives in that repo; cross-project
knowledge/strategy lives in the **suite root** (`Documents/Projects/boojy/`, the container that holds
the repo subfolders).

- **In each repo:** `CLAUDE.md`, `.claude/rules/`, `dreams.md` (§1), `.claude/` (settings, hook,
  skills), `README.md`, `CHANGELOG.md` (only once it ships releases), optional `FEATURES.md`, and
  `docs/` (`ROADMAP` · `BACKLOG` · `FEATURE_TRACKER` for apps · `ARCHITECTURE` · `archive` · `reviews`).
- **In the suite root:** `README.md`, `VISION.md`, and the shared **`CLAUDE.md`**; supporting docs
  (this file, `REPO_TEMPLATE.md`, `BRAND.md`) live in the root `docs/`. Retired docs → `archive/`
  (local-only). (Operational status lives in the vault — see the header.)

`CLAUDE.md` / `.claude/rules` / `dreams.md` can't move out of their repo — Claude Code reads them
from the repo and the hook uses repo-relative paths.

---

## Part A — the pieces

The *model* (always-true file roles + the committed-vs-probabilistic dividing line) is in the
suite-root `CLAUDE.md`. This is just the per-file roster:

- **`CLAUDE.md`** (repo) — authoritative, always-true local rules (architecture, commands, gotchas).
  Keep tight; suite-wide process inherits from the suite-root `CLAUDE.md`.
- **`.claude/rules/`** — one topic per file. `paths:` frontmatter is *aspirational*: conditional
  loading is unreliable in early-2026 Claude Code (loads globally regardless of dir #16299; injects
  on read not write #23478; user-level `paths:` ignored #21858). Treat as organization, not context
  savings; keep genuinely global rules in `CLAUDE.md`.
- **`dreams.md` (§1 only)** — the Active Engineering Target + a `- [ ]` / `- [x]` milestone checklist.
  Volatile working state; safe to wipe each milestone.
- **`.claude/hooks/post-edit-validation.sh`** — the per-edit gate (graceful-skip + `mktemp`). On
  failure it prints to stderr + exits non-zero. It does **not** write to any doc.
- **`.claude/settings.json`** — `compactPrompt` + the PostToolUse hooks (the Bash docs-nudge + the
  Edit/Write gate).
- **auto memory + `git log`** — learnings + history. Skim `/memory` after a big refactor.
- **`README.md` / `FEATURES.md` / `CHANGELOG.md`** — outward-facing. No CHANGELOG until an app has
  users; keep existing ones that track real releases.

---

## Part B — onboarding a repo into the shape

### Target skeleton

The canonical file/folder layout — every slot, which are always-present vs stub-allowed, and the
naming conventions (`SPEC-`, `IDEAS.md`, dated reviews) — lives in **[`REPO_TEMPLATE.md`](REPO_TEMPLATE.md)**.
One home for scaffold structure: read it when standing up a new repo. This section covers only the one
thing that varies per repo — the gate.

### The one variable: the gate

| Repo | Stack | Hook gate (per source edit) |
|------|-------|-----------------------------|
| boojy-design | Vite/React/TS + Vitest | `biome check --write` → `pnpm typecheck` (.ts/.tsx) → `vitest related` |
| boojy-notes | Vite/React/TS + Vitest | same trio |
| boojy-web | Astro static | `astro check` (scoped to `website/`); Biome lint separate |
| boojy-audio | Flutter + Rust | `.dart` → `flutter analyze`; `.rs` → `cargo check`/`clippy` (in `engine/`). Full `cargo test` / `flutter test` stay manual/CI, not in the per-edit loop |
| boojy-cloud *(TODO)* | Supabase edge fns | _suggested:_ minimal — `deno check`/`deno lint`, else no gate |

### Steps

Apply on a branch; **plan + diffs before deleting/rewriting**; green gates before commit; never
commit to the default branch; skip steps for files a repo doesn't have.

1. **`CLAUDE.md`** — trim to local-only always-true rules; suite-wide process inherits from the
   suite-root `CLAUDE.md`. Move per-area gotchas to `.claude/rules/`.
2. **`.claude/rules/`** — split gotchas one-topic-per-file (`paths:` where file-specific; global ones
   stay in `CLAUDE.md` or a no-`paths` rule file).
3. **`dreams.md`** — reduce to §1; relocate overflow (roadmap → `docs/ROADMAP.md`, backlog →
   `docs/BACKLOG.md`, durable gotchas → `.claude/rules/`), don't delete it.
4. **hook** — keep the gate + graceful-skip + `mktemp`; failures print to stderr + exit non-zero; no
   doc writes.
5. **CHANGELOG** — don't add until the app has users; keep existing ones that track real releases.
6. **Verify** — trigger the hook on a test edit (still gates), run `/memory` (CLAUDE.md + rules load,
   auto memory on), and note what auto memory already captured.

---

## Deferred — cross-repo propagation

"Update the logo everywhere" still has no channel. Planned first step once it bites: a
"Cross-cutting directives" section in `SUITE_STATUS.md` with per-app checkboxes + a "check it at
session start" line in each `CLAUDE.md`. Heavier options (a shared `@boojy/brand` package; a
SessionStart hook injecting directives) wait until drift actually hurts.
