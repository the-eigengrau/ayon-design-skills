# ayon-design-skills

A marketplace of production-grade skills to help you design and spec product with Claude Code against a serious craft bar.

## Skills

| Skill | What it does |
| --- | --- |
| **gather-inspiration** | Gather top-tier UI/UX inspiration: production-app screenshots, agency-grade style tiles, or a written UX recommendation. |
| **figma-to-prototype** | Turn a Figma design into a high-fidelity, interactive Next.js + Tailwind prototype, verified in a real browser. |
| **design-review** | Review a running UI's visual and interaction design against a strict craft bar; reports findings and a prioritized fix plan. |
| **write-prd** | Write or revise a PRD in a tight, intuition-first style on a standard product-spec template; lands it in a Linear project or in chat. |

## Install

Add the marketplace once:

```
/plugin marketplace add the-eigengrau/ayon-design-skills
```

Then install everything at once (recommended):

```
/plugin install everything@ayon-design-skills
```

Or pick individual skills à la carte:

```
/plugin install gather-inspiration@ayon-design-skills
/plugin install figma-to-prototype@ayon-design-skills
/plugin install design-review@ayon-design-skills
/plugin install write-prd@ayon-design-skills
```

Pull future updates with:

```
/plugin marketplace update
```

## How skills are namespaced

An installed skill invokes as `/<plugin>:<skill>`. The same skill therefore has a different name
depending on how you installed it:

- via its own plugin: `/design-review:design-review`
- via the bundle: `/everything:design-review`

So **don't install both** an à la carte plugin *and* `everything` for the same skill. It's
harmless, but you'll see the skill under two namespaces and wonder about the duplicate. Pick one
install path.

## Repo layout

```
ayon-design-skills/
├── .claude-plugin/marketplace.json     # the catalog
└── plugins/
    ├── design-review/
    │   ├── .claude-plugin/plugin.json
    │   └── skills/design-review/        # SKILL.md + references/
    ├── figma-to-prototype/
    │   ├── .claude-plugin/plugin.json
    │   └── skills/figma-to-prototype/
    ├── gather-inspiration/
    │   ├── .claude-plugin/plugin.json
    │   └── skills/gather-inspiration/
    └── write-prd/
        ├── .claude-plugin/plugin.json
        └── skills/write-prd/             # SKILL.md + references/
```

The `everything` plugin reuses those same skill folders via a `strict: false` catalog entry, so no
files are duplicated.

## License

[MIT](./LICENSE) © 2026 Ayon Bhattacharya. Use, modify, and redistribute freely, including
commercially. The one condition: keep the copyright and license notice so the originals stay
credited to the author.
