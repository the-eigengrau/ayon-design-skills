---
name: design-review
description: >-
  Review the visual and interaction design quality of a running UI against a strict craft bar
  (Linear / Vercel / Stripe / Airbnb; Dieter Rams "less, but better") and report findings plus a
  prioritized plan to fix them. Use WHENEVER the user asks to "do a design review", "review my
  UI / design / screen / page / app", "critique this design", "audit the UX", "is this well
  designed?", "does this look good?", "polish or QA the frontend", "give design feedback", or
  shares a localhost / deployed URL and wants design or UX feedback — even if they never say
  "design review". This grades the RENDERED, running interface, not code correctness (that's
  code-review): it verifies in a real browser, screenshots key screens and zoomed components,
  clicks through key flows as a user to exercise every interaction state, then judges against
  fixed UI standards (hierarchy, typography, spacing, elevation, color, motion, consistency) and
  UX heuristics (feedback, forgiveness, recognition-over-recall, error prevention) and writes up
  issues with a fix plan.
---

# Design review

Review a **running, rendered** interface the way a demanding design lead would, then report what's
wrong and how to fix it. The bar is **less, but better** (Dieter Rams): subtle, restrained,
considered — the quality of Linear, Vercel, Stripe, Airbnb. If a choice wouldn't survive their
review, it doesn't survive yours.

Two tiers of criteria, applied differently:

- **UI standards** — craft fundamentals. **Enforce unconditionally; they don't bend with style.**
- **UX heuristics** — usability principles. Apply with judgment for the product's context.

You **review and recommend** — you don't redesign or implement fixes unless the user asks. End with
a plan and offer to do the work.

Work in order. The failures in this task come from reviewing blind, reviewing statically, or
producing vague findings — the steps below exist to prevent exactly those.

## 1. Frame the review — don't review blind

Pin down three things from what the user said, the code/design around you, or **1–2 sharp questions**
when you genuinely can't infer them:

- **What to review** — the URL or local app, and how to reach it. If it's a dev server that isn't
  running, start it (the project's run/dev command, or the `run` skill) or ask the user to — *you
  cannot review what you cannot see.*
- **Key screens** — the handful of views that carry the product. Don't try to review everything;
  review what matters.
- **The primary job** — what is the user here to *do*? The main action on each screen anchors the
  whole hierarchy and UX judgment.

## 2. Open it in a real browser

Verification is non-negotiable and must happen in a browser. Use whatever control you have, in
roughly this order:

1. The Claude Chrome extension, or the `superpowers-chrome:browsing` skill / `use_browser` MCP tool.
2. Any other browser-automation MCP (Playwright/Puppeteer).
3. If you have none, **say so plainly** and tell the user how to open the URL themselves — then work
   from screenshots they provide. Never fabricate what the UI looks like.

## 3. Look hard — whole screens, zoomed parts, and live interaction

A design review is not a static screenshot pass. Do all of this:

- **Capture each key screen whole**, then **zoom into the components** — buttons, inputs, cards,
  nav, tables. Inspect type, spacing, borders, and shadows up close; that's where craft lives or
  dies. Keep the shots as evidence to cite in the report.
- **Squint test.** Blur your eyes or shrink the screenshot until detail drops out. Does **one**
  primary action still dominate? If two things fight, or nothing leads, hierarchy is broken.
- **Click through every key flow as a user** — and trigger the states you can't see at rest:
  hover controls, **tab through with the keyboard** to check focus, press/hold for active, open an
  **empty** list, submit an **invalid/empty** form to see the **error**, watch for **loading**.
  Missing states are the most common defect and only surface when you interact.
- **Watch motion.** Does it clarify cause and effect or just decorate? Is it quick (~150–250ms for
  small UI)? Toggle `prefers-reduced-motion` and confirm it's respected.
- **Check a narrow and a wide viewport** for layout integrity (light touch unless asked for more).

## 4. Grade against the rubric

Walk every screen against both tiers. Be specific about *where* each issue is and *which* item it
violates.

### UI standards — enforce unconditionally

- **Subtlety** — less but better. Nothing overdesigned. When in doubt it should be removed, not added.
- **Hierarchy** — one obvious primary action; a deliberate order of attention; survives the squint
  test. If everything is emphasized, nothing is.
- **Typography** — a constrained scale (**4–5 sizes from one ratio**), **one or two families**, body
  **line-height ~1.5** at a **60–75ch measure**; tighter tracking and lower line-height on large
  display text.
- **Layout & spacing** — everything on a shared spacing scale (**4px base**); align to a grid, don't
  eyeball; consistent rhythm. Misalignment by even a pixel reads as amateur.
- **Elevation** — model it as distance from a **single, consistent light source**: lighter surfaces
  come forward, lift via shadow; **larger shadow = more lift**. Keep shadows subtle and elegant —
  never heavy or muddy.
- **Color** — **≤3 hues, often fewer**; a neutral ramp does most of the work. **Exactly one
  interactive brand color, reserved for the primary action** so it never stops meaning "click me."
  Structural color ≠ interactive color.
- **Interaction states** — every clickable element has a **full set**: hover, focus, active,
  disabled, selected, loading — plus **empty** states wherever relevant.
- **Motion** — clarifies cause and effect, not decoration; **duration matches distance** (~150–250ms
  for small UI); **ease-out for entrances**; **respects `prefers-reduced-motion`**.
- **Consistency** — repeated elements look and behave identically; radii, padding, and gaps come
  from the scale, not per-component guesses.

### UX heuristics — apply with judgment

- **Recognition over recall** — show options and current state instead of forcing memory; **labels
  beat icons-alone** for ambiguous actions (while staying minimal and elegant).
- **Feedback** — every action gets a visible response within **~100ms** (even just a pressed/loading
  state); nothing should feel like it went nowhere.
- **Forgiveness** — destructive actions are confirmable or undoable; **prefer undo** over a confirm
  dialog where feasible.
- **Match the mental model** — labels and flow order use the **user's** language, not the system's
  internal structure.
- **Reduce choices per step** — defer or hide secondary actions; one screen, one main job.
- **Error prevention, then good errors** — disable or guide *before* failure; when errors happen,
  say what went wrong and how to fix it, **near where it happened**.
- **Respect state** — preserve input on error, remember scroll position, don't reset filters on
  navigation.

## 5. Report findings + a plan

Write it up so the user can act immediately. Structure:

1. **Verdict** — 2–3 sentences: the overall read against the bar, the biggest strength, the biggest
   risk. Be honest, not flattering.
2. **Findings**, grouped by severity (lead with the worst):
   - **Blocker** — breaks the core job, or egregiously fails a UI standard.
   - **Major** — clearly hurts usability or craft.
   - **Minor** — noticeable but low-cost.
   - **Polish** — subtle refinement toward the bar.

   Each finding names **where** (screen + the screenshot), **which standard/heuristic** it violates,
   **why it matters** (user impact), and the **concrete fix**. Example:

   > **Major — Hierarchy (Dashboard header).** Three header buttons (New, Import, Share) share the
   > brand-blue fill, so the squint test shows three equal targets and nothing reads as primary
   > [`dashboard-header.png`]. *Fix:* keep one brand-filled primary (New); demote Import and Share
   > to neutral/ghost buttons.

3. **Plan** — a prioritized sequence: **quick wins** (high impact, low effort) first, then deeper
   changes. This is the roadmap, not a restatement of the findings.

Then offer to implement the top items. See `references/report-template.md` for a full worked example
of the format and the level of specificity to hit.

## Common failure modes

- **Reviewing blind.** Grading from the code, the Figma, or a screenshot you didn't take, instead of
  opening the running UI. Open it and interact; if you truly can't, say so.
- **Static-only review.** Judging resting screenshots without clicking through — so you miss
  hover/focus/loading/empty/error states and feedback gaps. Trigger every state.
- **Vague findings.** "Improve the hierarchy" with no location, no evidence, no fix. Every finding
  cites where, which standard, and the concrete change.
- **Bending UI standards to taste.** Excusing color sprawl, weak alignment, or a missing primary as
  "the style." UI standards hold unconditionally; only UX heuristics flex with context.
- **A flat dump.** Thirty equal-weight nitpicks. Prioritize by severity; lead with what matters; let
  small stuff be small.
- **Over-reaching the brief.** Redesigning, or implementing fixes unprompted. Deliver the review and
  plan; build only when asked.
- **Praise-only or savage-only.** Both are useless. Name the real strengths and the real problems,
  each specific and located.
- **Skipping the squint test.** Cataloging pixel details while the screen has no clear primary
  action. Check hierarchy first — it's the finding that matters most.
