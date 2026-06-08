---
name: write-prd
description: Write or revise a PRD (Product Requirements Document) on the standard template in a tight, intuition-first style. Use this WHENEVER the user says "draft a PRD", "write a PRD", or "write up requirements", or asks to write up, scope, outline, or spec a feature or product idea into a structured doc by any name: PRD, product spec, one-pager, product brief, requirements doc, or the text that fills a Linear project's description. Trigger even when they never say "PRD" and only say "write up this feature", "scope this out", "draft a spec", "turn these notes into a spec", or "put it on our template". Also trigger to tighten or revise an existing draft. Do NOT trigger to summarize or shorten a finished PRD, write status updates or meeting notes, break work into Jira tickets or user stories, or implement a feature in code. If the Linear MCP is connected, write the result into the target project's description; otherwise output it in chat.
---

# Write a PRD

Produce a PRD that is **tight and intuition-first**, on the standard template. This works two ways: draft a new PRD from a feature idea or rough notes, or revise an existing draft up to the bar.

Filling the template is the easy part. The value of this skill is the **voice**: concision and intuition, applied as a deliberate edit pass. A draft that merely fills the sections is not done. The edit pass is where it becomes good, so always run it.

## The two principles

**Concision.** Every sentence has to earn its place. The reader is a busy PM, eng lead, or exec who skims. Cut rhetorical flourish, marketing closers, scaffolding labels, speculative roadmap, and explanations of why a metric matters when it is obvious. The goal is not "short," it is *dense*: say the true, specific thing once and move on.

**Intuition.** The reader should *feel* how the product works, not be told about it abstractly. This comes from concreteness: scenarios that read like a real exchange, real numbers instead of vague claims, and real product flows and field names instead of invented ones. A PRD earns intuition when a reader who has never seen the feature can picture using it.

## Output: where the PRD goes

A PRD is almost always meant to land in a project tracker, not just the chat.

- **If the Linear MCP is connected**, write the finished PRD into the target project's `description`. Identify the project from context, and ask the user which one if it is not obvious. Send Markdown with literal newlines (no escaped `\n`). Two cautions:
  - If the project already has a real description (not an empty stub), show the user what is there and confirm before overwriting. Do not clobber someone else's writeup.
  - If no matching project exists, ask whether to create one or just output in chat. Do not create a duplicate of an existing project.
- **If the Linear MCP is not connected**, output the finished PRD directly in chat as Markdown.

Either way, run the edit pass before you publish. The version that lands in Linear should already be tight.

## The template

Use these sections in this order, and keep the headings.

**Customer Messaging** — A few sentences on what is being built, in customer-facing language. Lead with the value and how it feels to use, then state the solution concretely. Stop when the point is made; no marketing closer.

**Problem Alignment**
- *The Problem* — The problem or opportunity, why it matters to users and the business, and the core insight you are operating on. Usually 2 to 3 problems, each a bold one-line claim followed by a sentence of support. End on the single sharp insight that motivates the solution.
- *Customer scenarios* — Concrete, named scenarios: who (practice area, role), where in the case lifecycle, and the actual interaction. Show the exchange, not a summary. This is where intuition lives or dies (see the voice rules below).

**Goals & Success** — The metrics you intend to move, defined operationally and precisely, tied to real tracked metrics and core initiative goals. Do not invent metrics to sound complete. Skip the explanation when the metric speaks for itself.

**Non-Goals** — Real, product-specific things a reader might reasonably assume are in scope but are not. Skip generic strawman disclaimers ("not rebuilding the engine") that no one would assume anyway.

**Solution Alignment**
- *Solution Overview* — 1 to 2 sentences on the high-level direction.
- *Key Features* — A short list in priority order, each a bold name followed by one line. Flag open questions inline as sub-bullets rather than pretending completeness.

## Voice: the edit pass

After the draft, run this pass. These rules are reverse-engineered from real edits, and each has a reason. Apply the reason, not the letter.

### Mechanics
- **No em-dashes.** This is the most reliable tell. Recast every one: a colon to introduce an explanation or list, a comma for a short aside, or a period to split into two sentences. The em-dash reads as a verbal tic, and the recast forces a cleaner structure.
  - *"agents now live where you already work — chat"* becomes *"agents now live where you already work: in chat"*
  - *"siloed from chat — our most-used surface"* becomes *"siloed from chat, our most-used surface"*
  - *"already happen in chat — we just aren't capturing them"* becomes *"already happen in chat. We just aren't capitalizing on them."*
- Parentheses, not dashes, for a true aside: *"(say, several providers with missing bills)"*.
- Plain, active, declarative sentences. Prefer the pragmatic verb (*"capitalizing on"* over *"capturing"*).

### Concision
- **Cut the marketing closer.** A punchy rhetorical sentence at the end of a paragraph ("No separate setup flow, no leaving the matter."; "no template required") almost always goes. It adds rhythm, not information.
- **Cut redundant examples.** If example queries appear in the scenarios, do not also list them up in The Problem. Say it in the one place it lands hardest.
- **Cut scaffolding.** Drop "(priority order)", "Primary / Secondary" labels, and speculative "Later / not in v1" lists unless the user asked for a roadmap. Structure should be felt, not announced.
- **Cut metric editorializing.** "This is the project's headline metric" and "by making chat the entry point" are throat-clearing. Define the metric and stop.

### Intuition
- **Scenarios are exchanges, not commands.** Write the user input the way a real user would type it (a natural question, *"what records are still missing"*, not a tidy imperative *"chase the missing records"*). Then show the agent's realistic response, including when it answers *no* before offering to act. The back-and-forth is the point: it demonstrates the product's judgment.
  - *Draft:* asks to "get the missing employment dates." The agent clarifies, then calls the client.
  - *Better:* asks "Do we have missing employment dates from the plaintiff?" The agent says no, but offers to call the client to gather them.
- **Use real numbers.** *"77%+ of users use chat every day"* beats *"users already use chat."* If you do not have the number, get it or leave a flagged blank. Do not paper over it with a vague claim.
- **Ground in the real product.** Name the actual editable fields (goals, knowledge, channel), the actual entry points (the manual card, proactive flows), the actual metrics. Invented specifics ("edit the script") read as fluent but are wrong, which is worse than vague.

### Honesty (it is a living doc)
- **Flag open questions inline.** A sub-bullet like *"Need specific examples of when to suggest each agent"* beats silent omission or invented filler. A PRD that admits what is unresolved is more trustworthy than one that fakes completeness.
- **Do not invent to sound complete.** Cut any metric, non-goal, or feature you cannot ground. If it matters and you do not know it, ask the user.

## Process

1. **Ground first.** Before drafting, gather the real inputs: the tracked metrics, the real product flows and field names, usage numbers, and the case-lifecycle context. Ask the user for anything you cannot verify. This prevents fluent-but-wrong specifics, the most common failure mode.
2. **Draft on the template.** Get every section down.
3. **Run the edit pass above.** This is non-optional and is where most of the quality lives. Then read it once more as a skimming exec: does every sentence earn its place, and can a stranger picture using the feature?

For a full gold-standard PRD and a before/after of the edits that got it there, read `references/example.md`.
