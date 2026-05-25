---
name: gather-inspiration
description: >-
  Gather top-tier UI/UX design inspiration for a design task — screenshots of real
  production apps (Linear, Stripe, Vercel, Coinbase, Airbnb, Gumroad and peers) saved
  to an inspiration folder, plus agency-grade style tiles for aesthetic/landing-page
  work, or a UX recommendation for interaction work. Use whenever the user asks to
  "gather inspiration", find design references/examples, do competitive UI research,
  explore an aesthetic or visual direction, mood-board, build style tiles, or see how
  top apps handle a specific screen / flow / interaction — even if they don't say
  "inspiration". Prefers the Mobbin MCP when installed; otherwise drives a browser tool
  (use_browser / Claude Chrome extension / Playwright). Never uses Dribbble/Behance-tier
  sources.
---

# Gather Inspiration

Collect **relevant, top-tier** design inspiration for whatever the user is building, and turn it into something they can act on. The job is not "find pretty screens" — it's *find the most applicable inspiration from the best production apps in the world, for this specific task and aesthetic.*

There are three deliverables. Pick based on the task (see **Route to a mode**). Don't do all three by default.

---

## 1. Frame the task first

Never start capturing blind. First pin down three things — from what the user said, the code/design files around you, or by **asking 1–2 sharp questions** when underspecified:

- **Surface** — what is being designed? A single component, a full screen, a multi-step flow, a landing/marketing page, or an interaction/animation?
- **Constraints** — platform (web / iOS / Android / desktop), density (data-heavy vs. spacious), the *real content* shown (e.g. "a gallery of agent templates at the top, then a config form"), and any existing design system to stay consistent with.
- **Aesthetic** — the style direction. If the user named one, honor it. If not, infer from their product or ask.

**Style → source mapping** (full catalog in `references/sources.md`):

| If the style is… | Look at… |
|---|---|
| Elegant / minimal / refined | Linear, Vercel, Stripe, Mercury, Things, Notion |
| Expressive / bold / neo-brutalist | Gumroad, Figma brand, Framer, Val Town |
| Premium / luxury / editorial | Apple, Teenage Engineering, Rivian, Aether |
| Dev-tool / technical / dense | Raycast, Linear, Railway, Resend, Supabase, Arc |
| Fintech / trust / data-dense | Stripe, Mercury, Ramp, Brex, Coinbase, Wise |
| Consumer / friendly / approachable | Airbnb, Duolingo, Headspace, Pitch, Cash App |

> **Example.** User: *"Gather inspiration for the creation wizard for an agent — there's a list of templates at the top."* → Surface: multi-step **creation flow** with a **template gallery**. Ask only what you can't infer: *"Web or native? Any aesthetic target, or should I match your current product?"* Then pull template-gallery + multi-step-setup screens from Notion, Vercel, Linear, Framer, v0, Gamma — the apps that do exactly this surface well.

---

## 2. Route to a mode

- **Mode A — Reference shots.** Task is *"build X"* or *"how do top apps do X?"*. → Gather **5–12** relevant screenshots into the inspiration folder. This is the default for concrete components, screens, and flows.
- **Mode B — Style tiles.** Task is about *look & feel*: a landing page, a brand/visual direction, "what should this *feel* like", "figure out the aesthetic". → Produce **1–3** original, agency-grade style tiles. Usually pull a few Mode-A shots first to ground them. See `references/style-tiles.md`.
- **Mode C — UX / interaction.** Task is about *behavior*: an animation, gesture, state transition, or flow logic ("how should drag-to-reorder feel?"). → Deliver a **written UX recommendation** (possibilities → recommendation → interaction spec), backed by a few reference captures of how the best apps solve it.

Modes combine (a landing page often wants A + B). When the deliverable is ambiguous, confirm in one line before spending effort.

---

## 3. Detect the capture tool (priority order)

1. **Mobbin MCP** — if any `mobbin*` tool is available, **prefer it.** It indexes real shipped app screens and flows, so it's unbeatable for *in-app* surfaces (onboarding, settings, wizards, empty states). Use whatever search/browse/capture tools it exposes — search by app, flow, or UI element, then save the relevant screens.
2. **Browser-control tool** — otherwise use the best available: `use_browser` (superpowers-chrome), the Claude Chrome extension, or Playwright/Puppeteer MCP. Best for *marketing/landing* pages and any live site. (`use_browser` drives an existing Chrome session over CDP — if it isn't responding, the user may need `/reload-plugins` after installing superpowers-chrome.)
3. **Nothing available** — say so and offer the fastest fix, e.g. *"Install the Mobbin MCP for in-app screens, or run `/plugin install superpowers-chrome@superpowers-marketplace` for live-site capture."* Don't fabricate screenshots.

Use Mobbin for *in-app* truth; use the browser for *public/marketing* aesthetic. For a landing page, the browser is primary; for a settings screen, Mobbin is.

---

## 4. Capture cleanly (Mode A)

Save everything under **`inspiration/<task-name>/`** in the current project (e.g. `inspiration/agent-creation-wizard/`). Task subfolders keep multiple gathers from colliding.

For each shot:
- **Dismiss the chrome** — accept/close cookie banners, newsletter modals, and nav popovers before capturing. Wait for the page to fully load (fonts, images, lazy sections).
- **Frame the actual UI** — scroll to the relevant section and capture *that*, not a half-loaded hero or a screen full of cookie banner.
- **Name it meaningfully** — `linear-project-create.png`, `stripe-pricing-tiers.png` — not `screenshot1.png`. The filename is the first layer of the index.
- **Stay on target** — every shot must earn its place against a stated constraint. A gorgeous screen that doesn't match the surface or style is clutter, not inspiration.

Then write **`inspiration/<task-name>/index.md`**: one row per shot with the **filename**, the **source URL**, and a **one-line "why it's relevant"** tied to the constraint. Close with a short synthesis: the patterns worth borrowing and your recommendation.

---

## 5. Style tiles (Mode B)

Read `references/style-tiles.md` and use `references/style-tile-template.html`. The loop, in short:

1. Ground the direction(s) with a few Mode-A reference shots.
2. Copy the template once per direction into `inspiration/<task-name>/style-tiles/<direction>.html`.
3. Reskin via the CSS variables — **swap in a distinctive type pairing**, set a cohesive palette, real sample copy, components, and **one composed in-context vignette** so it reads as *designed*, not a token dump.
4. **Render the `.html` in the browser, take a full-page screenshot, and look at it.** Self-critique against the quality bar. Iterate until it would pass as a slide in a top studio's brand deck.
5. **Only then** present the screenshots (+ HTML) for review. Never show a style tile you haven't rendered and inspected.

Make **1** tile when the direction is clear; **2–3** when contrasting directions will help the user decide.

---

## 6. UX / interaction recommendation (Mode C)

Capture a few references of how the best apps handle the interaction (animated GIFs/screen recordings if the tool supports them, else key-frame stills). Then write a recommendation with three parts:

1. **Possibilities** — the 2–4 viable interaction patterns, each with who does it well.
2. **Recommendation** — which one fits *this* product and why.
3. **Interaction spec** — the concrete feel: trigger, states, motion (durations/easing), affordances, edge cases (empty, error, reduced-motion).

Save references + the writeup in the task folder.

---

## Quality bar — top-tier or nothing

This is the whole point of the skill. **Only real production apps with elite design.** Linear, Stripe, Vercel, Coinbase, Airbnb, Gumroad, Mercury, Raycast, Apple, Notion — and peers at that level. **Never** Dribbble, Behance, Pinterest, template marketplaces, or AI-generated galleries (full denylist in `references/sources.md`). Concept art and contest shots aren't production-tested; real shipped UI is.

---

## Common failure modes

- **Low-tier drift.** Reaching for Dribbble/Behance/Pinterest because they're easy to search. Don't — go to the actual product (live site or Mobbin).
- **Pretty but irrelevant.** Collecting beautiful screens that don't match the surface or constraint. Every asset ties to the task.
- **Dirty captures.** Cookie banners, half-loaded pages, or nav chrome instead of the UI. Dismiss, wait, scroll, then capture.
- **Showing un-rendered style tiles.** Presenting tiles you never screenshotted. Always render → screenshot → critique → iterate first.
- **AI-slop tiles.** Inter/Arial defaults, purple-gradient-on-white, lorem ipsum. Use distinctive type, real copy, a cohesive palette with a clear dominant + accent.
- **Wrong volume.** 5–12 shots, 1–3 tiles. More isn't better; relevance is.
- **Token-dump tiles.** A tile that's just swatches and fonts with no composed vignette reads as a spec, not a design. Always include the in-context sample.
- **Mode confusion.** Building style tiles when they wanted reference shots (or vice versa). Confirm the deliverable when unclear.
- **Skipping framing.** Capturing before identifying constraints on an underspecified ask. Ask first.
- **No provenance.** Always record source URLs in the index — these are references for inspiration, not original work to claim.
