# Changelog — Boojy Suite (umbrella repo)

Decision and structure changes to the suite-level docs. Each app keeps its own `CHANGELOG.md`.

## 2026-09-07

### Improvements
- **Planning files pruned to one shape.** `SUITE_STATUS.md`, its generator script and the `weekly`
  and `suite-status` skills are gone (the Sunday ritual last ran in June); the README apps table is
  the one cross-suite status. `docs/DEV_SYSTEM.md` folded into `docs/REPO_TEMPLATE.md`, which now
  describes the Notes shape: one `docs/BACKLOG.md` per repo, no `dreams.md`, no roadmap or feature
  tracker. `AGENTS.md` docs model, release steps and Claude Code notes updated to match. Audio keeps
  its older shape until development resumes.
- **Contribution policy simplified** (`CONTRIBUTING.md`, `README.md`, `VISION.md` §8). Boojy is a
  personal project and isn't accepting external code contributions; no "opens at v1.0" promise.
  Feedback and bug reports go by email to tyr@boojy.org. The same text is in every public repo.
- **Cloud position revised** (`VISION.md` §0, §1, §3, §5, §7; `README.md`; `SUITE_STATUS.md`).
  The apps and every editing feature stay free forever, including commercial use, and local use
  never needs an account. Boojy Cloud becomes a *possible future service* with a small free storage
  allowance, where extra hosted storage could be paid for — payment covers hosting, never unlocks
  features. Connecting your own cloud storage is a separate future option. Cloud support would
  arrive app by app, with no date promised. Replaces the 2026-06-09 "no paid tier" and 2026-08-24
  "free-only if it returns" decisions. Notes Beta is unaffected (desktop, local files, no account,
  no sync).
