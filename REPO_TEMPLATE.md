# Boojy Repo Template

The canonical answer to **"what does a standard Boojy repo contain?"** — the file/folder layout, which
slots are always-present vs stub-allowed, and the naming conventions. Scaffold a new app from this
(e.g. *"set up a new repo per `REPO_TEMPLATE.md`"*).

This doc describes **structure only**. It *references* content rather than restating it, so it can't
drift: the shared process/conventions live in the suite-root [`CLAUDE.md`](CLAUDE.md), the strategy
and licensing decision in the [Vision doc](<Boojy Suite — Vision (2026 Refresh).md>), and the
docs-system shape + per-repo gate in [`DEV_SYSTEM.md`](DEV_SYSTEM.md).

## The skeleton

```
<repo>/
├── README.md                 # dev/public-facing: what it is, stack, scripts
├── CLAUDE.md                 # app-specific always-true rules; inherits the suite-root CLAUDE.md
├── dreams.md                 # §1 only — active engineering target + milestone checklist
├── CHANGELOG.md              # once the app ships releases (not before)
├── LICENSE                   # GPLv3 for apps (see Vision §8); boojy-cloud stays private
├── .claude/
│   ├── settings.json         # compactPrompt + PostToolUse hooks
│   ├── settings.local.json   # GITIGNORED — personal settings
│   ├── rules/*.md            # one per-area gotcha topic; paths: frontmatter where file-specific
│   ├── hooks/                # gate only (e.g. post-edit-validation.sh)
│   └── skills/*/SKILL.md     # repo-local skills
└── docs/
    ├── ROADMAP.md            # ordered intentions
    ├── BACKLOG.md            # unscheduled someday
    ├── FEATURES.md           # plain-language tour (user-facing apps)
    ├── ARCHITECTURE.md       # system design, folder structure
    ├── FEATURE_TRACKER.md    # built-vs-not checklist (user-facing apps)
    ├── archive/              # superseded plans, old milestones/reviews
    ├── private/              # GITIGNORED — sensitive strategy, secrets pointers, business docs
    └── reviews/              # dated deep-review reports
```

## Naming conventions

- **`docs/SPEC-<name>.md`** — a *binding architectural constraint* (load-bearing, supersedes feature
  requests). E.g. boojy-notes' `docs/SPEC-markdown-source-of-truth.md`. Use this prefix, not a bespoke
  filename, so future binding specs are discoverable.
- **`docs/IDEAS.md`** — the lightweight parking lot for mid-work design/feature ideas (distinct from
  `BACKLOG.md`, which is committed someday-work).
- **`docs/reviews/<type>_YYYY_MM_DD.md`** — dated reviews, underscores, type-first
  (`codebase_review_2026_06_01.md`, `ui_ux_review_2026_05_30.md`, `code_quality_2026_03_24.md`).

## How to apply it

- **Stub-allowed.** Any slot may be a near-empty stub when there's nothing real yet — keep the
  *structure* uniform and fill on demand. Don't block a repo on a doc it has nothing to say in.
- **Parity is not required.** A younger or smaller app legitimately has fewer rules, skills, or docs
  than boojy-audio. Same *slots*, different *fill* — **don't manufacture files for symmetry**
  (boojy-design's thin `.claude/skills`, boojy-cloud's missing `docs/` tree are correct, not gaps).
- **Delegator exception.** A repo whose real app lives in a subfolder (boojy-web → `website/`) keeps
  the kit at the repo root, but its source — and some docs — live in the sub-app folder.
- The **one thing that varies per repo is the gate** (the per-edit hook command for its stack) — see
  the table in [`DEV_SYSTEM.md`](DEV_SYSTEM.md).
