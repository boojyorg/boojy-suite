---
name: weekly
description: Sunday weekly review + planning ritual for the Boojy suite. Reviews the past week across all repos (facts from git), collects Tyr's reflections, then co-drafts next week's "This Week" list into the vault's SUITE_STATUS.md. Invoke on Sunday (or whenever the This Week list is from a past week).
---

# /weekly — suite review & planning ritual

Two-sided weekly loop: **Claude brings the facts** (what actually happened across the repos),
**Tyr brings the judgment** (how the week felt, where the priority pull is). Both propose targets;
Tyr approves; the result replaces "This Week" in `~/Documents/Vault/Boojy/SUITE_STATUS.md`.

The list is **disposable** — the review lives in this conversation, not in an archive. Targets are
one-line pointers; detail stays in each repo's `dreams.md` / `ROADMAP.md`.

## Procedure

### 1. Gather (automatic — no questions yet)

- Run `boojy-web/scripts/suite-status.sh` to refresh the snapshot.
- Read `~/Documents/Vault/Boojy/SUITE_STATUS.md` — the outgoing "This Week" list and week heading.
- Compute the week boundaries: outgoing week's Monday, and next Monday (`date -v+mon +%Y-%m-%d`).
- Per repo (boojy-audio, boojy-design, boojy-notes, boojy-web, boojy-cloud, suite root):
  - `git log --since "<outgoing Monday>" --oneline` on the default branch *and* the current branch
  - current branch + dirty-file count
  - merged PRs this week: `gh pr list --state merged --search "merged:>=<outgoing Monday>"`
  - ⚠️ stacked-PR check (root `CLAUDE.md`): a "MERGED" badge may mean merged into a stack base, not
    master — verify anything load-bearing with `git merge-base --is-ancestor`.
- For each outgoing target: **done / partial / not started**, with one line of evidence.

### 2. Claude's review (~1 screen, outcomes first)

What shipped (user-visible first), what stalled and why it seems stalled, leftover targets,
surprises (red CI, stranded branches, uncommitted work older than a week). Honest, not performative
— if the week's work didn't match the week's plan, say so plainly.

### 3. Tyr's review (open conversation, not a form)

Ask open questions and wait: How did the week feel? Anything the facts above miss? What's pulling
at you for next week? Anything on the list that should be dropped rather than carried?

### 4. Co-propose next week

Draft **3–6 one-line, app-prefixed targets** from: leftovers worth carrying (mark them
*carry-over*), each repo's `dreams.md` / `docs/ROADMAP.md`, and Tyr's stated pull. Where Claude's
proposal differs from Tyr's, say why once — then defer (low-stakes). Tyr edits/approves the final
list before anything is written.

### 5. Write

Replace the "This Week" section with `## This Week — w/c <next Monday>` + the approved targets.
Keep "Parked" only for items still genuinely parked. Refresh the per-app **Focus** sections where
reality moved. Do **not** archive the old list.

### 6. Close

If the week surfaced durable cross-session learnings, save them to auto-memory. Do not commit or
push anything in the app repos as part of this ritual — it reads; it only writes the vault doc.
