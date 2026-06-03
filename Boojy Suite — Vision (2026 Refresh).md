# 🎨 Boojy Suite — Vision (2026 Refresh)

> **Tagline:** Creativity without limits.
> **Mission:** Make professional creative tools free, accessible, and ethical for everyone.
> **Status as of:** 2026-05-29 · **Supersedes:** *Boojy Suite (Vision Document)* and *Boojy Suite (Early Preview)*

---

## 0. What changed in this refresh

The original vision (Nov 2025 – Feb 2026) described a seven-app lineup that no longer matches what's being built. This refresh reconciles the vision with the actual repos:

- **Boojy Notes is now a core app.** It didn't exist in the original vision; it's currently the third active product (v0.4.0).
- **Boojy Draw is gone as a standalone app.** Its painting/illustration features were folded into **Boojy Design**.
- **Boojy Animate is no longer a standalone app.** Animation becomes a **future feature of Boojy Design**.
- **Boojy Score is not in the works.** It's a *possible* future feature of **Boojy Audio**, or a standalone app — but only **post-v1.0 Boojy Audio**, not now.
- The 30-month month-by-month roadmap from the original docs is retired; it no longer reflects reality. Status below is anchored to actual repo state instead.

---

## 1. Why Boojy exists

Creative software has become expensive, closed, and extractive — Adobe Creative Cloud at ~£66/month, paywalled "pro" tiers, proprietary file formats, and telemetry that monetises your work. For students, hobbyists, and independent creators that's prohibitive.

**Boojy Suite** is a creative ecosystem that is free forever (no subscriptions, paywalls, or trials), open-source after each app hits v1.0, privacy-first (no telemetry or ads by default), cross-platform, and ethical — revenue is reinvested into development rather than extracted from users.

---

## 2. Core principles

These are unchanged from the original vision and still hold:

1. **Free to create** — every app free forever, including commercial use; no feature gating.
2. **Open-source after v1.0** — apps go open once feature-complete and stable. **Apps: GPLv3** (copyleft, Blender-style). **Boojy Cloud stays private** (AGPLv3 if ever opened).
3. **Privacy-first** — no telemetry by default, no ads, no data selling.
4. **Human + AI development** — built by Tyr Bujac with AI tooling assisting; all creative and architectural decisions are human-made.
5. **Accessibility** — lightweight apps, intuitive UI (GarageBand/iMovie-level approachability), free for education, offline-capable.
6. **Community-driven** — feedback shapes priorities.

---

## 3. Product suite — actual lineup & status

| App | What it is | Replaces | Status (2026-05-29) | Tech |
|---|---|---|---|---|
| **Boojy Audio** | Cross-platform DAW: multi-track audio/MIDI, mixing, automation, VST3, export | GarageBand, Logic, Audition | **Active dev — v0.3.0 (alpha).** Highest priority. | Flutter (UI) + Rust engine via FFI |
| **Boojy Design** | Web image editor (raster + the former Draw feature set): paint, shapes, text, layers, transform, `.design` save | Photoshop, Affinity, Procreate, Canva | **MVP complete — v0.4.0.** Konva engine landed. | Web (TS), Konva canvas |
| **Boojy Notes** | Markdown note-taking, block editor, wikilinks, cloud sync | Notion, Obsidian (lightweight) | **In progress — v0.4.0.** Active. | Web + Electron, Supabase + R2 |
| **Boojy Video** | Video editing with integrated motion graphics | Premiere, Final Cut, Resolve | **Backlog — not started.** | TBD |
| **Boojy Cloud** | Creative-aware storage, sync, version history | — (infra) | **Backlog — low priority.** Last active Feb 2026. | Supabase |

### Folded-in / future features (not standalone apps)

- **Drawing/illustration** → lives inside **Boojy Design** (the former "Boojy Draw").
- **Animation** → planned **future feature of Boojy Design**, not a separate "Boojy Animate" app.
- **Music notation / scoring ("Score")** → **possible future feature of Boojy Audio, or a standalone app — post-v1.0 Audio only.** Not in active development.

### Companion / aspirational

- **Buddy Music** — free streaming + buy-to-own marketplace for indie artists (90/10 split), integrating with Boojy Audio. Still aspirational; not started. Kept in the vision as a long-term companion platform.

---

## 4. Adobe / competitor coverage (refreshed)

| Incumbent | Boojy replacement | Status |
|---|---|---|
| Audition / Logic / GarageBand | Boojy Audio | In active dev (v0.3.0) |
| Photoshop / Procreate / Canva | Boojy Design | MVP complete (v0.4.0) |
| Notion / Obsidian | Boojy Notes | In progress (v0.4.0) |
| Premiere / After Effects | Boojy Video | Backlog |
| Animate / Toon Boom | *Design (future animation feature)* | Not started |
| MuseScore / Sibelius | Boojy Audio (Score), possibly standalone | Not started |

---

## 5. Roadmap (reframed to reality)

Rather than fixed month numbers, priorities are now ordered by current state:

**Now**
- **Boojy Audio** — push v0.3.x toward Beta/v0.5; it's the highest-priority app.
- **Boojy Notes** — continue toward a stable release; polish the core editor and sync.
- **Boojy Design** — MVP is done; stabilise and begin scoping the **animation feature**.

**Next**
- Promote Audio and Design from alpha/MVP toward v1.0 (feature-complete + stable → open-source).
- Stand up **Boojy Cloud** properly once at least one app needs production-grade sync beyond Notes' current Supabase + R2 setup.

**Later / post-v1.0**
- **Animation** in Boojy Design.
- **Boojy Video** moves out of backlog.
- **Score** decision: feature of Boojy Audio vs. standalone app — evaluated only after Boojy Audio reaches v1.0.
- **Buddy Music** companion platform, if/when Audio is stable.

---

## 6. Platform strategy

**macOS-first.** macOS is the primary development and testing device, so it's the lead platform for every app — features land and stabilise on macOS first. Other platforms follow once a feature is solid on macOS.

- **Boojy Audio** — macOS lead (Flutter cross-platform, so Windows follows); mobile/iPad later.
- **Boojy Design** — web-first (browser), which is inherently cross-platform; tested on macOS.
- **Boojy Notes** — web + desktop (Electron), developed on macOS; mobile considerations in the codebase.

Windows, Linux, and tablet/mobile builds remain a "between v0.5 and v1.0" goal per app, but always after the macOS build is working.

---

## 7. Business model

**Low priority — Boojy is primarily a personal-use project.** There's no revenue ambition driving the roadmap; the apps are built for personal use and shared freely. A business model exists only to cover costs if/when others use the apps, not as a goal in itself.

If support is offered, it stays **optional and ethical**: a single paid cloud tier plus donations. Direct (website) billing is preferred over App Store billing to avoid the platform cut.

**Boojy Cloud — one paid tier for now: "Boojy Orbit."** Targeting ~10 GB storage (could change). A free tier likely sits below it. No multi-tier Plus/Pro/Max ladder for the moment — just Orbit.

---

## 8. Licensing

- **Apps: GPLv3** (decided). Copyleft, Blender-style — forks must stay open. The apps (Audio, Notes, Design, Web) carry a `LICENSE` of GPLv3; already-published commits stay under whatever they shipped (relicensing is forward-only). MIT was considered and rejected — copyleft keeps the suite and its forks open.
- **Boojy Cloud:** **private** for now (it's the one paid service and is tied to specific infra). If opened later, **AGPLv3** is the fit, not GPL — see reasoning below.
- **Trademarks:** "Boojy" name and logo protected; forks allowed under different names.

> **Note on Cloud:** the apps' GPLv3 license is independent of the server's. Apps talk to Cloud over a network API, and network use isn't "distribution," so a GPLv3 app does **not** force the server open. You can freely mix GPLv3 apps with a closed or AGPL backend.

---

## 9. Brand

Authoritative brand notes live in their own files alongside this doc (`Documents/Projects/boojy/`): see *Boojy Colors*, *Boojy Logos*, and *Boojy name* (platform handles: boojy.org, @boojy on YouTube, @boojyorg elsewhere, GitHub `boojyorg`).

---

> **Built by creators, for creators. — Tyr Bujac, Boojy Development**
>
> *This is the current source-of-truth vision. The original two suite docs are retained for history with superseded banners.*
