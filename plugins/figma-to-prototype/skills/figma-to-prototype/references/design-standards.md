# Design standards

The design language is **elegant, subtle, and minimal**. Exercise restraint. Do not over-design.
Dieter Rams: *less, but better.* When in doubt, remove rather than add. Apply these standards to
every screen and component you build.

## Hierarchy

Give each view one focused, clear focal point. The eye should know where to land first, then where
to go next. If everything is emphasized, nothing is — demote secondary and tertiary elements with
size, weight, and color so the primary action or content reads instantly.

## Layout & alignment

Be deliberate about spacing and layout. Favor a strong alignment wherever possible — shared edges
and a consistent grid read as intentional and calm. Use a consistent spacing rhythm (the spacing
tokens) rather than one-off values. Misalignment, even by a pixel, is the fastest way to look
amateur.

## Elevation

Be mindful of the *relative* elevation of surfaces. Elevation can be expressed by **shadows** or by
**surface color** — prefer subtlety in both:

- Lighter surfaces sit in the **foreground**; darker surfaces recede into the **background**.
- Bigger shadows indicate **more** elevation; small shadows indicate **less**.
- Keep a consistent elevation scale (e.g. base → card → popover → modal) and use it everywhere.

Avoid heavy, muddy shadows. A subtle, well-placed shadow communicates more than a large one.

## Color

Reason about color in a disciplined way, considering both **interaction** and **structure**, and be
consistent across the whole prototype:

- **No more than 3 hues** — and feel free to use fewer.
- Exactly **one interactive color** (typically also the brand color). Reserve it for things the
  user can act on; don't spend it on decoration.
- Use neutrals for structure (surfaces, borders, text) and let the single interactive color do the
  signalling.

## Design bar

Strive for the quality of teams like **Linear, Vercel, and Airbnb** — precise, restrained, and
considered. If a choice wouldn't survive their review, it doesn't survive yours.

## Tokens

Maintain shared tokens between Figma and the front-end. Be mindful of naming and structure: the
token vocabulary on both sides should match so a designer and an engineer are speaking the same
language. Every visual value in the UI should resolve through a named token, never a literal.
