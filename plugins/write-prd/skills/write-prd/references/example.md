# Worked example: a gold-standard PRD

This is a real, finished PRD in the target voice. Read it for the feel of the whole, then study the before/after pairs below to see the edits that got it there. The "before" in each pair is a competent first draft; the "after" is the shipped version. The gap between them is the entire skill.

---

## Gold-standard PRD: Chat-based comms agents

**Customer Messaging**

Comms agents now live where you already work: in chat. Describe what you need in plain language and the agent plans it with you: it asks the few clarifying questions it needs, drafts the call/text plan inline, and lets you revise it just by replying. When Eve spots a comms need in your conversation (say, several providers with missing bills) it offers to handle the follow-up by phone.

### Problem Alignment

#### The Problem

Two gaps cap how much value comms agents deliver today:

1. **Planning real comms is a conversation, not a form.** Anything past a trivial call needs back-and-forth to scope: which providers, what to ask, what counts as done. The current setup asks for all of that up front in a rigid flow, so users either over-specify or abandon it.
2. **Comms agents are siloed from chat, our most-used surface.** Chat is where attorneys and case managers already reason through a matter. Comms agents live elsewhere, so most users never discover them. Right now discoverability, not capability, is the ceiling on adoption.

Insight: the planning conversation and the discovery moment both already happen in chat. We just aren't capitalizing on them.

#### Customer scenarios

* A **PI case manager** at a plaintiff firm, mid-treatment, types "what records are still missing." The agent asks which providers and confirms the deadline, then plans calls to the three facilities with open requests.
* An **attorney prepping discovery responses** asks Eve "Do we have missing employment dates from the plaintiff?" The agent says no, but offers to call the client to gather them.
* A **case manager on a new MVA matter** asks "do we have an open claim yet? Has the insurer accepted liability?" The agent confirms the claim but says we aren't clear on liability yet, and offers to call and confirm.

#### Goals & Success

* **Activation:** lift the % of matters where a user places a call with a comms agent.
* **Attach rate:** lift the % of matters where the user has created a comms agent.

#### Non-Goals

* Not auto-executing comms; a human still approves every plan before it runs.
* Not removing the standard manual comms agent flow (e.g. click on the card).
* Not removing proactive comms flows.

### Solution Alignment

#### Solution Overview

Make chat a first-class control surface for comms agents: plan, edit, launch, and get nudged toward agentic comms where appropriate, all inside the matter chat 77%+ of users already use every day.

#### Key Features

1. **Clarifying questions before planning:** the agent asks only the questions it needs, in chat, then proposes a plan.
2. **Edit comms plans in chat:** reply to revise contacts, goals, knowledge, channel, or timing instead of reopening a form.
3. **Kick off ad hoc comms from chat:** kick off calls or texts from a plain-language request.
4. **Proactive agent suggestions:** Eve detects a comms-shaped need in the conversation and offers the matching agent.
   1. Need specific examples of when to suggest each of our major comms agents: case updates, discovery info gathering, claims opening & follow-up, treatment check-ins.

---

## Before / after: the edits that matter

### Customer Messaging closer

> **Before:** ...it offers to handle the follow-up by phone. **No separate setup flow, no leaving the matter.**
>
> **After:** ...it offers to handle the follow-up by phone.

The closer is rhythm, not information. Cut it.

### The Problem, claim 1

> **Before:** Anything past a trivial call **— "follow up on the records we're still missing," "gather the discovery facts from the plaintiff" —** needs back-and-forth to scope...
>
> **After:** Anything past a trivial call needs back-and-forth to scope...

The inline examples are redundant with the scenarios, and the em-dashes go. Trust the reader and let the example land once, later.

### The insight line

> **Before:** ...both already happen in chat **—** we just aren't **capturing** them.
>
> **After:** ...both already happen in chat**.** We just aren't **capitalizing on** them.

Em-dash becomes a period. The pragmatic verb ("capitalizing on") is sharper than the soft one ("capturing").

### A scenario

> **Before:** An attorney prepping discovery responses asks Eve to **"get the missing employment dates from the plaintiff." The agent clarifies the exact facts needed, then calls the client to gather them.**
>
> **After:** An attorney prepping discovery responses asks Eve **"Do we have missing employment dates from the plaintiff?" The agent says no, but offers to call the client to gather them.**

This is the most important edit. The user input becomes a question a person would actually type, and the agent answers like the real product would (it says *no* first, then offers to act). The reader now sees the product's judgment, not a sanitized command-to-execution.

### Goals & Success

> **Before:**
> - **Primary — comms-agent activation:** lift the % of matters where a user starts an agent, by making chat the entry point. This is the project's headline metric (Activation Rate, Case Comms [Q2 2026]).
> - **Secondary — attach rate:** more agents per active matter, driven by proactive in-chat suggestions.
> - **Secondary — time-to-first-plan:** planning in chat should beat the structured setup flow...
>
> **After:**
> - **Activation:** lift the % of matters where a user places a call with a comms agent.
> - **Attach rate:** lift the % of matters where the user has created a comms agent.

Three compounding moves: drop the Primary/Secondary scaffolding, cut the editorializing ("by making chat the entry point", "This is the project's headline metric"), and delete the invented metric ("time-to-first-plan") that isn't actually tracked. What remains is two metrics defined operationally and precisely.

### Non-Goals

> **Before:**
> - Not rebuilding the voice/call engine.
> - Not auto-executing comms...
> - Not removing the structured setup flow...
> - Not inbound/triage, SMS-specific work, or new practice areas.
>
> **After:**
> - Not auto-executing comms; a human still approves every plan before it runs.
> - Not removing the standard manual comms agent flow (e.g. click on the card).
> - Not removing proactive comms flows.

Strawman non-goals ("not rebuilding the engine") go: nobody assumed that. The real non-goals are product-specific worries someone on the team would actually raise: that this new chat entry point might replace the existing manual and proactive entry points. Name those instead.

### Solution Overview specificity

> **Before:** ...all inside the matter chat **users already use.**
>
> **After:** ...all inside the matter chat **77%+ of users already use every day.**

A real number does the persuading that a vague phrase only gestures at.
