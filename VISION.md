# 🎨 Boojy Suite — Vision (2026 Refresh)

> **Tagline:** Creativity without limits.
> **Mission:** Make creative tools that are free, friendly, and a joy to use — built for hobbyists, not professionals.
> **Status as of:** 2026-09-11 · **Supersedes:** *Boojy Suite (Vision Document)* and *Boojy Suite (Early Preview)*

---

## 0. What changed in this refresh

### 2026-09 refresh — Cloud position revised

- **The apps stay free forever, including commercial use, and local use never needs an account.** This is the promise everything else sits under; it is restated, not changed.
- **Boojy Cloud is a possible future service, not a dropped one.** If built, it would offer a small free storage allowance, and extra hosted storage could be paid for — payment covers hosting, never unlocks features. This deliberately replaces the 2026-06-09 "no paid tier" and 2026-08-24 "free-only if it returns" decisions (see §7).
- **Connecting your own cloud storage** (a Drive or iCloud folder, for example) is a separate future option.
- Cloud support would arrive **app by app**; nothing implies it exists today or promises a date. **Notes Beta is unaffected:** desktop, local files, no account, no sync.

### 2026-08 refresh — direction reset

- **Hobbyist, not professional.** Boojy makes friendly creative tools for hobbyists — approachable like GarageBand or iMovie, not feature-race competitors to Logic or Photoshop. The mission no longer says "professional".
- **No generative AI in the products** — new core principle (see §2).
- **Release order is now Notes → Audio → Design → Video.** Notes is the first app pushed to a public release; Audio resumes after.
- **Boojy Cloud is dropped for now.** Its only app consumer (Notes sync) was removed in the desktop-only push; the service is being wound down. It can return if an app ever needs production-grade sync.
- **Suite continuity is an explicit goal:** one icon set (Lucide), one design language (`docs/BRAND.md`), shared UI components where the stacks allow (Notes / Design / boojy.org are all React); Audio mirrors the tokens and patterns in Flutter.

### 2026-06 refresh — reconciling with reality

The original vision (Nov 2025 – Feb 2026) described a seven-app lineup that no longer matches what's being built. This refresh reconciles the vision with the actual repos:

- **Boojy Notes is now a core app.** It didn't exist in the original vision; it's currently the third active product (v0.8.0).
- **Boojy Draw is gone as a standalone app.** Its painting/illustration features were folded into **Boojy Design**.
- **Boojy Animate is no longer a standalone app.** Animation becomes a **future feature of Boojy Design**.
- **Boojy Score is not in the works.** It's a *possible* future feature of **Boojy Audio**, or a standalone app — but only **post-v1.0 Boojy Audio**, not now.
- The 30-month month-by-month roadmap from the original docs is retired; it no longer reflects reality. Status below is anchored to actual repo state instead.

---

## 1. Why Boojy exists

Creative software has become expensive, closed, and extractive — Adobe Creative Cloud at ~£66/month, paywalled "pro" tiers, proprietary file formats, and telemetry that monetises your work. For students, hobbyists, and independent creators that's prohibitive.

**Boojy Suite** is a creative ecosystem whose apps are free forever (no subscriptions, paywalls, or trials for any app or editing feature), open-source (GPLv3, developed in public repos), privacy-first (no telemetry or ads by default), cross-platform, and ethical — revenue is reinvested into development rather than extracted from users.

---

## 2. Core principles

Principles 1–6 are unchanged from the original vision and still hold; 7 was added in the 2026-08 refresh:

1. **Free to create** — every app free forever, including commercial use; no feature gating.
2. **Open source, GPLv3** — the app repos are public on GitHub (`boojyorg`) and developed in the open; v1.0 marks feature-complete and stable, not the moment the source opens. **Apps: GPLv3** (copyleft, Blender-style). **Boojy Cloud stays private** (AGPLv3 if ever opened). *(Originally "open-source after v1.0"; the repos went public during development in mid-2026.)*
3. **Privacy-first** — no telemetry by default, no ads, no data selling.
4. **Human + AI development** — built by Tyr Bujac with AI tooling assisting; all creative and architectural decisions are human-made.
5. **Accessibility** — lightweight apps, intuitive UI (GarageBand/iMovie-level approachability), free for education, offline-capable.
6. **Community-driven** — feedback shapes priorities.
7. **No generative AI** — Boojy apps ship nothing that writes, draws, or composes for you; what you make in a Boojy app is made by you. Assistive, non-generative processing (e.g. noise removal) is judged case-by-case. Distinct from principle 4: AI assists the suite's *development*, never the user's creative work.

---

## 3. Product suite — actual lineup & status

Ordered by release order: **Notes → Audio → Design → Video.**

| App              | What it is                                                                                                      | For people who don't need…            | Status (2026-08-24)                                                          | Tech                               |
| ---------------- | ---------------------------------------------------------------------------------------------------------------- | ------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------- |
| **Boojy Notes**  | Markdown note-taking: your files on disk, wikilinks, fast desktop app                                           | Notion, Obsidian                      | **Active — v0.8.0, desktop-first.** First app headed for a public release.   | React + Vite + Electron            |
| **Boojy Audio**  | Cross-platform DAW: multi-track audio/MIDI, mixing, automation, VST3, export                                    | GarageBand, Logic, Audition           | **Paused at v0.6.0 (since June 2026)** — v0.7 "Devices & Feel" resumes after Notes releases. | Flutter (UI) + Rust engine via FFI |
| **Boojy Design** | Web image editor (raster + the former Draw feature set): paint, shapes, text, layers, transform, `.design` save | Photoshop, Procreate, Canva           | **MVP complete — v0.4.0, stable.** Konva engine landed.                      | Web (TS), Konva canvas             |
| **Boojy Video**  | Video editing with integrated motion graphics                                                                   | iMovie, Premiere, Resolve             | **Backlog — not started.** Last in the release order.                        | TBD                                |

### Folded-in / future features (not standalone apps)

- **Drawing/illustration** → lives inside **Boojy Design** (the former "Boojy Draw").
- **Animation** → planned **future feature of Boojy Design**, not a separate "Boojy Animate" app.
- **Music notation / scoring ("Score")** → **possible future feature of Boojy Audio, or a standalone app — post-v1.0 Audio only.** Not in active development.
- **Cloud sync ("Boojy Cloud")** → **a future possibility, not a current product.** The 2026 Supabase + R2 service was wound down (the private repo stays). If built, it arrives app by app, with no date promised — see §7.

---

## 4. Coverage — the tools you might not need

Boojy apps aren't drop-in replacements for professional suites — they're for people whose needs those suites exceed. If you make things for the joy of it, you may not need:

| If you were reaching for…     | Try                                      | Status                          |
| ----------------------------- | ---------------------------------------- | ------------------------------- |
| Notion / Obsidian             | Boojy Notes                              | Active (v0.8.0) — releasing first |
| GarageBand / Logic / Audition | Boojy Audio                              | Paused at v0.6.0 — next after Notes |
| Photoshop / Procreate / Canva | Boojy Design                             | MVP complete (v0.4.0)           |
| iMovie / Premiere             | Boojy Video                              | Backlog                         |
| Animate / Toon Boom           | *Design (future animation feature)*      | Not started                     |
| MuseScore / Sibelius          | Boojy Audio (Score), possibly standalone | Not started                     |


---

## 5. Roadmap (reframed to reality)

Rather than fixed month numbers, priorities follow the release order: **Notes → Audio → Design → Video.**

**Now**

- **Boojy Notes** — the release push: desktop-first polish and stability toward the suite's first public release.
- **Suite continuity groundwork** — design language + tokens in `docs/BRAND.md`, Lucide everywhere, shared UI components across the React apps (Notes / Design / boojy.org).

**Next**

- **Boojy Audio** — resume after the Notes release; v0.7 "Devices & Feel" is mid-flight.
- **Boojy Design** — stabilise; scope the **animation feature** when it gets focus again.

**Later / post-v1.0**

- **Boojy Video** moves out of backlog (last in the release order).
- **Animation** in Boojy Design.
- **Score** decision: feature of Boojy Audio vs. standalone app — evaluated only after Boojy Audio reaches v1.0.
- **Boojy Cloud** — a possible future service, added app by app if it is built; no date (§7).

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

**Hosted storage is the one thing that could ever cost money.** **Boojy Cloud** is a possible future service, not a current product. If it is built, it would offer a small free storage allowance, and extra hosted storage could be paid for — payment covers hosting, never unlocks features. Connecting **your own cloud storage** (a Drive or iCloud folder, for example) is a separate future option. Cloud support would arrive app by app; nothing here implies it exists today or promises a date. No price or quota is set or published.

*(Decided 2026-09-07. Replaces the 2026-06-09 "no paid tier" and 2026-08-24 "free-only if it returns" decisions; the earlier Supabase + R2 service was wound down in August 2026 and the private repo is dormant.)*

---

## 8. Licensing

- **Apps: GPLv3** (decided). Copyleft, Blender-style — forks must stay open. The apps (Audio, Notes, Design, Web) carry a `LICENSE` of GPLv3; already-published commits stay under whatever they shipped (relicensing is forward-only). MIT was considered and rejected — copyleft keeps the suite and its forks open.
- **Boojy Cloud:** **private** for now (tied to specific infra). If opened later, **AGPLv3** is the fit, not GPL — see reasoning below.
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

