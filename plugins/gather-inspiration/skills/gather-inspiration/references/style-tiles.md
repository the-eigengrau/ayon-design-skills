# Style tiles

A **style tile** sits between a moodboard and a full comp: it communicates the *visual atmosphere* of a UI — color, type, components, texture, voice — without committing to a page layout. It lets the user react to a direction fast, before any screens are designed.

Use `style-tile-template.html` as the starting point. It's self-contained and reskins entirely through CSS variables at the top.

## How many

- **1 tile** — when the direction is already clear and you're showing the user *what it will feel like*.
- **2–3 tiles** — when contrasting distinct directions will help the user *choose* (e.g. "Refined" vs. "Expressive" vs. "Editorial"). Make them genuinely different — different type pairing, palette, and mood — not three shades of the same idea.

## The build loop

1. **Ground it.** Pull a few Mode-A reference shots first so the direction is rooted in real top-tier work, not invented from nothing.
2. **Copy the template** per direction → `inspiration/<task>/style-tiles/<direction-name>.html`.
3. **Reskin via the CSS variables** at the top of the file: palette, fonts, radii, shadows. Fill in:
   - **Brand adjectives** — 3 words that name the feeling.
   - **A distinctive type pairing** — load real fonts (Google Fonts `<link>` is already wired). A characterful display face + a clean body face. Never the Inter/Arial/system default.
   - **Color palette** — a clear dominant, supporting neutrals, and *one* confident accent. Cohesive, not a rainbow.
   - **Components** — buttons, input, card, badge, toggle, rendered from the tokens.
   - **Effects** — gradient, shadow scale, radius scale, grain/glass note.
   - **One composed in-context vignette** — a small hero or product card built from the tokens. This is what makes it read as *designed* rather than a spec sheet. Do not skip it.
   - Real sample copy throughout. No lorem ipsum.
4. **Render & inspect.** Open the file in the browser tool (`file://<absolute-path>`), set a wide viewport (~1440px), and take a **full-page screenshot** to `inspiration/<task>/style-tiles/<direction-name>.png`. Then actually *look at it*.
5. **Self-critique** against the bar below. Fix and re-render until it passes.
6. **Present** the screenshots (and HTML) for review. Never show a tile you haven't rendered and inspected.

## Quality bar — would this pass as a slide in a top studio's brand deck?

- Clean grid; generous, consistent spacing; nothing cramped or touching edges.
- Type pairing is distinctive and the scale is harmonious; headings have presence.
- Palette is cohesive — clear dominant + one accent; neutrals are intentional, not default gray.
- Consistent radii and a single coherent shadow language throughout.
- Components look crisp and real — correct contrast, aligned, properly sized hit areas.
- The vignette looks like a slice of a real product, not a swatch.
- **In the screenshot:** no overflow, no overlap, no clipped text, no unloaded fonts/images.

## Anti-slop checklist

- ❌ Inter / Roboto / Arial / system font as the headline face.
- ❌ Purple gradient on white (the canonical AI-slop look).
- ❌ Lorem ipsum.
- ❌ Evenly-distributed rainbow palette with no dominant.
- ❌ Inconsistent corner radii / mismatched shadows.
- ✅ One bold, intentional aesthetic point of view, executed precisely.

## Rendering notes

- `use_browser` controls an existing Chrome session — open the local `file://` path in a tab, wait for fonts to load, then capture full-page. If fonts look wrong, the Google Fonts `<link>` didn't load yet; wait and re-capture.
- Keep each direction in its own `.html` so screenshots stay 1:1 with files.
