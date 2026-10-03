# 🎨 Boojy Suite — Vision (2026 Refresh)

> **Tagline:** Creativity without limits.
> **Mission:** Make creative tools that are free, friendly, and a joy to use — built for hobbyists, not professionals.
> **Status as of:** 2026-10-01 · **Supersedes:** *Boojy Suite (Vision Document)* and *Boojy Suite (Early Preview)*

---

## 0. Where things stand (2026-10)

- **Release order: Notes → Audio → Design → Video.** Notes and Audio are in early access and are
  the focus. **Boojy Design is on hold** until both are in Beta: its repo is private and it isn't
  online.
- **The apps stay free forever**, including commercial use, and local use never needs an account.
- **Boojy Cloud is planned, not a current product:** work starts after the Notes Beta (§7).

How the vision got here (the 2026-06, 2026-08 and 2026-09 refreshes) is in git history
(`git log -p VISION.md`); the decisions themselves are in the sections below.

---

## 1. Why Boojy exists

Creative software has become expensive, closed, and extractive — Adobe Creative Cloud at ~£66/month, paywalled "pro" tiers, proprietary file formats, and telemetry that monetises your work. For students, hobbyists, and independent creators that's prohibitive.

**Boojy Suite** is a creative ecosystem whose apps are free forever (no subscriptions, paywalls, or trials for any app or editing feature), open-source (GPLv3, developed in public repos), privacy-first (no telemetry or ads by default), cross-platform, and ethical — revenue is reinvested into development rather than extracted from users.

---

## 2. Core principles

Principles 1–6 come from the original vision; 7 was added in 2026-08:

1. **Free to create** — every app free forever, including commercial use; no feature gating.
2. **Open source, GPLv3** — the app repos are public on GitHub (`boojyorg`) and developed in the open; v1.0 marks feature-complete and stable, not the moment the source opens. **Apps: GPLv3** (copyleft, Blender-style). **Boojy Cloud stays private** (AGPLv3 if ever opened). *(Originally "open-source after v1.0"; the repos went public during development in mid-2026.)* **Exception:** an app on hold may go private until it resumes — Boojy Design, since 2026-10.
3. **Privacy-first** — no telemetry by default, no ads, no data selling.
4. **Human + AI development** — built by Tyr Bujac with AI tooling assisting; all creative and architectural decisions are human-made.
5. **Accessibility** — lightweight apps, intuitive UI (GarageBand/iMovie-level approachability), free for education, offline-capable.
6. **Community-driven** — feedback shapes priorities.
7. **No generative AI** — Boojy apps ship nothing that writes, draws, or composes for you; what you make in a Boojy app is made by you. Assistive, non-generative processing (e.g. noise removal) is judged case-by-case. Distinct from principle 4: AI assists the suite's *development*, never the user's creative work.

---

## 3. Product suite — actual lineup & status

Ordered by release order: **Notes → Audio → Design → Video.**

| App              | What it is                                                                                                      | For people who don't need…            | Status (2026-10-01)                                                          | Tech                               |
| ---------------- | ---------------------------------------------------------------------------------------------------------------- | ------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------- |
| **Boojy Notes**  | Markdown note-taking: your files on disk, wikilinks, fast desktop app                                           | Notion, Obsidian                      | **Early access — v0.12.0, desktop-first.** Next stage: the desktop Beta.   | React + Vite + Electron            |
| **Boojy Audio**  | Cross-platform DAW: multi-track audio/MIDI, mixing, automation, VST3, export                                    | GarageBand, Logic, Audition           | **Early access — v0.6.0, in active development.** Slowed from mid-September; resumed 2026-09-29 to finish v0.7.0, reliability first. | Flutter (UI) + Rust engine via FFI |
| **Boojy Design** | Web image editor (raster + the former Draw feature set): paint, shapes, text, layers, transform, `.design` save | Photoshop, Procreate, Canva           | **On hold — v0.4.0 working preview.** Until Notes and Audio are in Beta; repo private, not online. | Web (TS), Konva canvas             |
| **Boojy Video**  | Video editing with integrated motion graphics                                                                   | iMovie, Premiere, Resolve             | **Backlog — not started.** Last in the release order.                        | TBD                                |

### Folded-in / future features (not standalone apps)

- **Drawing/illustration** → lives inside **Boojy Design** (the former "Boojy Draw").
- **Animation** → planned **future feature of Boojy Design**, not a separate "Boojy Animate" app.
- **Music notation / scoring ("Score")** → **possible future feature of Boojy Audio, or a standalone app — post-v1.0 Audio only.** Not in active development.
- **Cloud sync ("Boojy Cloud")** → **planned, not a current product.** Work starts after the Notes Beta, Notes first; the principles are in §7. (The 2026 Supabase + R2 service was wound down; the private repo stays.)

---

## 4. Coverage — the tools you might not need

Boojy apps aren't drop-in replacements for professional suites — they're for people whose needs those suites exceed. If you make things for the joy of it, you may not need:

| If you were reaching for…     | Try                                      | Status                          |
| ----------------------------- | ---------------------------------------- | ------------------------------- |
| Notion / Obsidian             | Boojy Notes                              | Early access (v0.12.0)           |
| GarageBand / Logic / Audition | Boojy Audio                              | Early access (v0.6.0), in development |
| Photoshop / Procreate / Canva | Boojy Design                             | On hold (v0.4.0)                |
| iMovie / Premiere             | Boojy Video                              | Backlog                         |
| Animate / Toon Boom           | *Design (future animation feature)*      | Not started                     |
| MuseScore / Sibelius          | Boojy Audio (Score), possibly standalone | Not started                     |


---

## 5. Roadmap (reframed to reality)

Rather than fixed month numbers, priorities follow the release order: **Notes → Audio → Design → Video.**

**Now**

- **Boojy Notes** — early access since v0.7.0; daily-use reliability and polish toward the desktop Beta.
- **Boojy Audio** — back in development (2026-09-29): finish v0.7.0, engine reliability first (the 2026-09-13 review in its `docs/reviews/`).
- **Suite continuity groundwork** — design language + tokens in `docs/BRAND.md`, Lucide everywhere, shared UI components across the React apps (Notes / boojy.org; Design when it resumes).

**Next**

- **Boojy Design** — resumes once Notes and Audio are both in Beta: stabilise, then scope the **animation feature**.

**Later / post-v1.0**

- **Boojy Video** moves out of backlog (last in the release order).
- **Animation** in Boojy Design.
- **Score** decision: feature of Boojy Audio vs. standalone app — evaluated only after Boojy Audio reaches v1.0.
- **Boojy Cloud** — after the Notes Beta: Notes first, then other apps join (§7).

---

## 6. Platform strategy

**macOS-first.** macOS is the primary development and testing device, so it's the lead platform for every app — features land and stabilise on macOS first. Other platforms follow once a feature is solid on macOS.

- **Boojy Audio** — macOS lead (Flutter cross-platform, so Windows follows); mobile/iPad later.
- **Boojy Design** — web-first (browser), which is inherently cross-platform; tested on macOS.
- **Boojy Notes** — desktop-first (Electron), developed on macOS; the web build is parked, mobile considerations remain in the codebase.

Windows, Linux, and tablet/mobile builds remain a "between v0.5 and v1.0" goal per app, but always after the macOS build is working.

---

## 7. Business model

**Low priority — Boojy is primarily a personal-use project.** There's no revenue ambition driving the roadmap; the apps are built for personal use and shared freely. A business model exists only to cover costs if/when others use the apps, not as a goal in itself.

**The apps are free forever.** Every Boojy app and every editing feature is free, including commercial use — no subscriptions, paywalls, trials, or feature gating. Local use never requires an account. Every app keeps your work as ordinary files in a folder you choose, so nothing depends on a Boojy service. If support for the project itself is ever needed, it stays **optional and ethical** — donations.

**Hosted storage is the one thing that could ever cost money**, and for now it doesn't: Boojy Cloud
starts free, with no paid tier.

### Cloud principles (decided 2026-10-02)

Boojy Cloud is planned, not built. These are the rules it's built to:

- **Boojy works without Boojy.** Every app keeps working, and your files stay usable, with every
  Boojy server switched off. Formats stay open and documented. Boojy should still be useful in 30
  years, even with nobody maintaining it.
- **Local-first; the cloud is a mirror.** The files on your devices are the real copy. If Boojy
  Cloud ever stops, syncing stops but nobody loses a note: every device already has them all.
- **End-to-end encrypted from day one.** Files and file names are encrypted on your device; Boojy
  can't read them, so there's nothing to hand over. What the server can still see (sizes, times)
  is stated plainly.
- **Free, with a cap that never shrinks.** It starts at **500 MB** (tens of thousands of notes).
  It can grow, never shrink. At the cap, sync pauses for new files; nothing is deleted.
- **No subscription for now.** A paid storage tier is only reconsidered after the Notes Beta, once
  sync works well and real users hit the cap. If it ever exists, it covers hosting only and comes
  with a public running-costs page.
- **You choose what syncs, from the first version.** Pick which folders sync (say, skip an
  archive of old lecture slides); the rest stays on that device only. Notes are tiny; slides,
  PDFs and textbooks are what fill the cap.
- **Your own storage is always an option.** A folder synced by iCloud, Syncthing or similar keeps
  working, on desktop and in the mobile apps' "choose a folder" setting.
- **Never take over the computer.** Boojy never moves files, changes system settings, or syncs a
  folder you didn't choose. Desktop defaults to local files; only the web app defaults to the
  cloud.
- **A couple of clicks.** Sign in with email and password (no Google or Apple sign-in), save a
  recovery key once, done. Each other device: sign in and your notes appear.
- **Trust you can check.** A public security write-up, a status page and a costs page; an
  independent review before the public launch. Opening the server code so anyone can run their
  own is the leaning, not yet decided (§8).

**Order:** Notes Beta → notes.boojy.org as a real web app → Cloud alpha (Tyr only) → invited beta →
iPad and Android apps → public. Ideas held for later: expiring end-to-end-encrypted share links for
"send me the project" (with Audio), and Finder integration once Video makes on-demand files matter.

*(Replaces the 2026-09-07 position, which allowed paid hosted storage from the start; that in turn
replaced the 2026-06-09 and 2026-08-24 decisions. The earlier Supabase + R2 service was wound down
in August 2026 and its private repo is dormant.)*

---

## 8. Licensing

- **Apps: GPLv3** (decided). Copyleft, Blender-style — forks must stay open. The apps (Audio, Notes, Design, Web) carry a `LICENSE` of GPLv3; already-published commits stay under whatever they shipped (relicensing is forward-only). MIT was considered and rejected — copyleft keeps the suite and its forks open.
- **Boojy Cloud:** **private** for now. Opening the new sync server (so anyone can self-host it) is the leaning (§7); if opened, **AGPLv3** is the fit, not GPL — see reasoning below.
- **Trademarks:** "Boojy" name and logo protected; forks allowed under different names.
- **Contributions: closed** (updated 2026-09-07; originally "closed during Early Access",
2026-06-11). Boojy is a personal project and doesn't accept external code contributions or pull
requests. That may change later; there's no date. Every public repo carries the same
`CONTRIBUTING.md`. Feedback and bug reports are welcome by email (tyr@boojy.org). If
contributions ever open, review contribution licensing first (for example whether a DCO or a
CLA is appropriate for GPLv3 code) before accepting the first external change.

> **Note on Cloud:** the apps' GPLv3 license is independent of the server's. Apps talk to Cloud over a network API, and network use isn't "distribution," so a GPLv3 app does **not** force the server open. You can freely mix GPLv3 apps with a closed or AGPL backend.

---

## 9. Brand

Authoritative brand facts (colors, logo conventions, name & handles: boojy.org, @boojy on YouTube, @boojyorg elsewhere, GitHub `boojyorg`) live in `**[docs/BRAND.md](docs/BRAND.md)`**; early ideation is archived locally in `archive/brand/`.

---

> **Built by creators, for creators. — Tyr Bujac, Boojy Development**
>
> *This is the current source-of-truth vision. The original two suite docs are retained for history with superseded banners.*

