# Design review & browser verification

Read this during step 5 (verification). The goal is to look at the running prototype the way a
demanding reviewer would and catch what's off *before* the user does.

## The Steve-Jobs-level bar

Don't ask "does this look roughly right?" Ask "is this indistinguishable from the source, and is it
a pleasure to use?" Scrutinize, in order:

1. **Fidelity to Figma.** Side-by-side with the reference image, does every frame match — layout,
   spacing, type, color, elevation? Note any deviation, however small.
2. **Hierarchy.** Does each view have one clear focal point? Does the eye land and move correctly?
3. **Alignment & spacing rhythm.** Are edges shared and the spacing consistent (tokens, not one-off
   values)? Any drift, even a pixel, fails.
4. **Elevation logic.** Lighter forward, darker back; shadow size tracks elevation; consistent
   scale across surfaces.
5. **Color discipline.** ≤3 hues, exactly one interactive color, used consistently and only where
   the user can act.
6. **Interaction polish.** Hover, focus, active, and transitions present and smooth. No dead-ends,
   no janky motion, no missing states.

## How to look

Use the available browser capability (`superpowers-chrome:browsing` / `use_browser` MCP, else
Claude's Chrome extension; if neither, describe how the user opens `localhost`).

1. Open the running prototype at `localhost`.
2. View each page **as a whole** — overall composition and balance.
3. Zoom into **each major component** — inspect spacing, type, borders, shadows up close.
4. **Interact with every flow** — click every control, hover, navigate between views; confirm
   transitions feel smooth and nothing breaks or dead-ends.
5. Compare against the Figma reference images frame by frame.

## Pass/fail checklist

Before declaring done, every line must pass:

- [ ] Each frame matches its Figma reference (layout, spacing, type, color, elevation).
- [ ] Every view has one clear focal point / hierarchy.
- [ ] Alignment is strong; spacing uses tokens, not one-off values.
- [ ] Elevation is consistent and subtle (lighter forward, darker back; shadow size = elevation).
- [ ] ≤3 hues; exactly one interactive color; used consistently.
- [ ] All interactive states present (hover/focus/active) and transitions smooth.
- [ ] Every flow clicks through end to end with no dead-ends.
- [ ] No hardcoded hex/px — all visual values resolve through named tokens.
- [ ] Nothing added that isn't in the source design.

If any line fails, fix it and look again with fresh eyes.
