---
name: figma-to-prototype
description: >-
  Translate a Figma design into a rich, fully interactive, ultra-high-fidelity code prototype
  with Next.js + Tailwind. Use this WHENEVER the user shares a Figma URL or link, or says things
  like "turn this design into code", "build a prototype from this mockup", "implement this design
  1:1", "make this Figma real", or mentions the Figma MCP / Figma Dev Mode — even if they never say
  "prototype" or "skill". The skill pulls structure and design tokens via the Figma MCP, maintains a
  shared Figma↔Tailwind token bridge, builds with restraint to a Linear / Vercel / Airbnb quality
  bar (Dieter Rams: "less, but better"), and verifies the result in a real browser against a
  Steve-Jobs-level design review. Reach for it on any design-to-code or mockup-to-prototype request.
---

# Figma → interactive prototype

Translate a Figma design into a working, interactive Next.js + Tailwind prototype that matches the
source pixel-for-pixel and clears a Steve-Jobs-level design review. This is a prototyping
codebase — favor speed and fidelity over infrastructure. Use fake data and mock APIs freely.

Work in this order. Do not skip ahead — most of the ways this task fails come from coding before
understanding the design.

## 1. Understand the design first — do not write code yet

Use the Figma MCP read tools, in roughly this order:

1. `get_metadata` — an XML overview of the file/page structure (node IDs, layer types, names,
   positions, sizes). Use it to map the design and find the node IDs of the frames you'll build.
   Omit `nodeId` to list the top-level pages first.
2. `get_design_context` — the primary design-to-code tool. For each frame node, returns reference
   code, a screenshot, contextual metadata, and asset download URLs. Adapt the reference code to
   Next.js + Tailwind; don't paste it verbatim.
3. `get_variable_defs` — the variable/token tree for a node (e.g. `color/brand/600: #4F46E5`,
   `space/4: 16`). This is your token source for step 2.
4. `get_screenshot` — a high-fidelity render of a node to compare your build against. Raise
   `maxDimension` to inspect fine detail.
5. `get_code_connect_map` — existing Figma-node → codebase-component mappings, if any. Reuse mapped
   components instead of rebuilding them.

All of these need a `fileKey` and `nodeId`. Extract both from the Figma URL the user provides:
`figma.com/design/:fileKey/:fileName?node-id=1-2` → `fileKey` = `:fileKey`, `nodeId` = `1:2`
(convert the `-` to `:`). If the URL has no `node-id`, ask the user for a node-specific link rather
than guessing.

Pull every relevant frame, its components and their variants, and the **full variable tree**.
Save the screenshots as your reference. *Why:* coding before you've read the token tree forces you
to guess values and invent structure — the single biggest source of drift from the source.

## 2. Build the token bridge before building UI

Map Figma variables → Tailwind theme tokens with shared, consistent names. Mirror Figma's naming
and grouping so a designer reading either side recognizes the same vocabulary. Cover colors,
spacing, radii, typography, and shadows.

*Why:* if you ever type a raw hex or pixel value inside a component, the semantic layer is missing.
Every visual value should resolve through a named token. Concrete mapping:

| Figma variable        | Tailwind token (`theme`)      | Usage in JSX                          |
| --------------------- | ----------------------------- | ------------------------------------- |
| `color/brand/600`     | `colors.brand.600`            | `className="bg-brand-600"`            |
| `space/4`             | `spacing.4` (16px)            | `className="p-4"`                     |
| `radius/md`           | `borderRadius.md`             | `className="rounded-md"`              |
| `elevation/card`      | `boxShadow.card`              | `className="shadow-card"`             |

Bad: `<div className="bg-[#4f46e5] p-[16px]">`. Good: `<div className="bg-brand-600 p-4">`.

## 3. Scaffold Next.js + Tailwind

Set up a minimal Next.js (App Router) + Tailwind project. Wire the token bridge into
`tailwind.config` / the theme. Keep it a prototype: fake data modules, mock API routes, no real
backend, no auth, no database. Don't over-engineer.

## 4. Implement exactly, component by component

Match spacing, alignment, elevation, and type to Figma — not approximately, exactly. Build the
real interactions: hover, focus, active, transitions, navigation, and the click-through flows the
design implies. Restraint over flourish; *less, but better*. Add nothing that isn't in the design.

Read `references/design-standards.md` and apply it throughout — it expands the design language
(hierarchy, layout, elevation, color discipline) that every screen must honor.

## 5. Verify in a real browser

Open the running prototype and look at it. Prefer, in order:

1. The `superpowers-chrome:browsing` skill / the `use_browser` MCP tool, if available.
2. Claude's standard Chrome extension.
3. If no browser capability exists, say so and tell the user how to open `localhost` themselves.

Look at each page as a whole **and** at each major component up close. Interact with every flow —
click, hover, navigate — and confirm transitions feel smooth and nothing dead-ends. Grade the
result against `references/design-review.md` before declaring anything done.

## 6. Iterate

Fix what the review surfaces and look again with fresh eyes. Repeat until it would pass a
Steve-Jobs-level review — not "looks close," but indistinguishable from the source and a pleasure
to use.

## Common failure modes

- **Coding before reading the design.** Pulling one frame, skipping the variable tree, then
  guessing values and inventing structure. Do step 1 fully first.
- **Hardcoded hex / px.** A raw value in a component means there's no real token bridge. Route
  every value through a named token.
- **Inventing content.** Adding sections, copy, or flourishes that aren't in the Figma. Match the
  source; restraint beats embellishment.
- **Approximating instead of matching.** "Close enough" spacing, type, or elevation reads as off.
  Match exact values from the tokens.
- **Color sprawl.** More than 3 hues, or more than one interactive color. Keep it disciplined.
- **Over-engineering.** Building a real backend, auth, or DB. Use mock data — this is a prototype.
- **Skipping verification.** Declaring done without opening a browser, or checking one screen and
  never interacting with the flows.
