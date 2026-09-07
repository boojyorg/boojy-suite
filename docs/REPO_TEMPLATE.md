# Boojy Repo Template

What a standard Boojy repo contains and how to stand one up. The rules every repo follows are in
the suite root's `AGENTS.md`; this file is the scaffold. Reshaped 2026-09-07 to the shape Boojy
Notes settled on: one planning file, no `dreams.md`, no roadmap or feature tracker.

## The skeleton

```
<repo>/
├── README.md                 # what it is, how to run it, a Status paragraph, a Contributing section
├── AGENTS.md                 # app-specific always-true rules; inherits the suite-root AGENTS.md
├── CLAUDE.md                 # symlink → AGENTS.md (Claude Code reads this name)
├── CHANGELOG.md              # `## Unreleased` + released versions (format in the suite-root AGENTS.md)
├── CONTRIBUTING.md           # the shared contribution policy, same text in every public repo
├── LICENSE                   # GPLv3 for apps (see Vision §8); boojy-cloud stays private
├── .claude/
│   ├── settings.json         # compactPrompt + PostToolUse hooks
│   ├── settings.local.json   # GITIGNORED — personal settings
│   ├── rules/*.md            # one per-area gotcha topic; `paths:` frontmatter where file-specific
│   ├── hooks/                # the per-edit gate only (e.g. post-edit-validation.sh)
│   └── skills/*/SKILL.md     # repo-local skills, if any
└── docs/
    ├── BACKLOG.md            # THE planning file: direction, next, known issues, someday, decisions
    ├── ARCHITECTURE.md       # optional — system design and folder structure (or keep it in AGENTS.md)
    ├── SPEC-<name>.md        # optional — a binding constraint (e.g. Notes' markdown-source-of-truth)
    ├── archive/              # superseded plans and old reviews
    ├── private/              # GITIGNORED — personal notes, sensitive material
    └── reviews/              # dated deep-review reports
```

A root `FEATURES.md` is optional: a plain-language tour for a user-facing app when the README's
feature list isn't enough (Boojy Design has one).

## Naming conventions

- **`docs/SPEC-<name>.md`** — a *binding architectural constraint* (load-bearing, supersedes feature
  requests). E.g. boojy-notes' `docs/SPEC-markdown-source-of-truth.md`. Use this prefix so future
  binding specs are discoverable.
- **Dated reviews** carry the date in the filename (`docs/reviews/codebase_review_2026_06_01.md`,
  or `docs/REVIEW-2026-09-06.md` for a one-off at the top of `docs/`). A review is a point-in-time
  report: once its items are accepted, declined or fixed, the residue goes to `BACKLOG.md` or
  `CHANGELOG.md` and the review is archived or deleted.

## The one thing that varies per repo: the gate

`.claude/hooks/post-edit-validation.sh` runs after every source edit. It keeps a graceful skip for
files it doesn't cover and a `mktemp` scratch file; on failure it prints to stderr and exits
non-zero. It never writes to any doc.

| Repo | Stack | Hook gate (per source edit) |
|------|-------|-----------------------------|
| boojy-notes | Vite/React + Vitest | Biome with fixes → `tsc` (.ts/.tsx) → `vitest related` |
| boojy-design | Vite/React/TS + Vitest | same trio |
| boojy-web | Astro static | `astro check` (scoped to `website/`); Biome lint is a separate gate |
| boojy-audio | Flutter + Rust | `.dart` → `flutter analyze`; `.rs` → `cargo check` + `clippy` (in `engine/`). Full test suites stay in CI |
| boojy-cloud | Supabase edge fns | none (dormant) |

`.claude/rules/*.md` `paths:` frontmatter is organisation, not a guarantee of conditional loading —
keep genuinely global rules in `AGENTS.md`.

## Standing up a new repo

Apply on a branch; green gates before commit; never commit to the default branch.

1. Copy the skeleton. Symlink `CLAUDE.md` → `AGENTS.md`.
2. `AGENTS.md`: local always-true rules only (stack, commands, invariants, where things live).
   Per-area gotchas go to `.claude/rules/`, one topic per file.
3. `docs/BACKLOG.md`: start it with a Direction section and a Next section, even if short.
4. The hook: pick the gate for the stack from the table above.
5. `CONTRIBUTING.md` copied verbatim from another repo; `CHANGELOG.md` from the first release.
6. Verify: trigger the hook on a test edit and confirm `AGENTS.md` + rules load in a fresh session.

## How to apply it

- **Stub-allowed.** Any slot may be a near-empty stub when there's nothing real yet — keep the
  *structure* uniform and fill on demand. Don't block a repo on a doc it has nothing to say in.
- **Parity is not required.** A younger or smaller app legitimately has fewer rules, skills, or docs.
  Same *slots*, different *fill* — don't manufacture files for symmetry.
- **Delegator exception.** A repo whose real app lives in a subfolder (boojy-web → `website/`) keeps
  the kit at the repo root; its source, and some docs, live in the sub-app folder.
- **boojy-audio** still carries the older shape (`dreams.md`, `docs/ROADMAP.md`, `FEATURE_TRACKER.md`,
  `IDEAS.md`, `plans/`). It moves to this shape when development resumes, not before.
