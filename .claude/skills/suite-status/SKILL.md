---
name: suite-status
description: Use when the user asks for the overall state of the Boojy suite, cross-project status, progress, or "what's next" mid-week. Refreshes the suite progress tracker. (For the Sunday review/planning ritual, use /weekly instead.)
disable-model-invocation: false
---

# Suite Status / Progress Tracker

The suite tracker is **`SUITE_STATUS.md` at the suite root** (public, tracked in boojy-suite).
Refresh it, then report.

```bash
./scripts/suite-status.sh
# or override the output path:
# ./scripts/suite-status.sh /absolute/path/to/SUITE_STATUS.md
```

It rewrites **only** the auto Snapshot block (version, branch, last commit, 30-day commits,
working-tree state per repo). The **This Week** list and per-app **Focus** notes are hand-maintained
and preserved across runs — never edit the AUTO block by hand.

After running: summarize what changed since last time (new commits, version bumps, dirty trees),
then point at the top unchecked This Week target as the recommended next action. Strategy/intent
lives in `VISION.md`; this tracker is operational state. If the This Week heading is from a past
week, suggest `/weekly` rather than editing the list ad hoc.
