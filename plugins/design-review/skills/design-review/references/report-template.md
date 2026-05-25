# Report template — a worked example

Read this to calibrate the **format** and the **level of specificity** your review should hit. This
is a sample review of an imaginary project-management app (a Dashboard + a "New project" modal),
written after opening it in a browser and clicking through the flow. Match this shape; don't copy
the content.

The bar for a finding: a stranger could open the app, find the exact spot, understand why it's a
problem, and make the fix — without asking you a single follow-up question.

---

## Verdict

Solid bones — the layout grid is consistent and the type is restrained — but the screen has **no
clear primary action**, and the create flow gives **no feedback on submit**, so it feels broken
even though it works. Biggest strength: clean, calm spacing rhythm. Biggest risk: a user can't tell
what to do first, or whether their click registered. Two fixes move this most of the way to the bar.

## Findings

### Blocker

**Feedback — New project modal, Create button.** Clicking **Create** does nothing visible for ~1.2s
while the request runs — no spinner, no disabled state, the button stays fully active
[`create-modal-submit.png`]. Users double-click, creating duplicate projects. *Why it matters:* an
action that looks like it went nowhere is indistinguishable from a bug. *Fix:* on click, switch the
button to a loading state (spinner + "Creating…", disabled) within 100ms; on success, close the
modal and toast "Project created."

### Major

**Hierarchy — Dashboard header.** Three header buttons (New project, Import, Templates) share the
same brand-blue fill, so the squint test shows three equal targets and nothing reads as primary
[`dashboard-header.png`]. *Why it matters:* the one thing most users come to do — create a project —
doesn't stand out. *Fix:* keep **New project** as the single brand-filled primary; demote Import and
Templates to neutral/ghost buttons.

**Color — global.** The brand blue is spent on decoration: section underlines, the active nav pill,
*and* primary buttons all use it [`dashboard-overview.png`, `settings.png`]. *Why it matters:* when
the interactive color also paints structure, it stops reliably meaning "click me." *Fix:* reserve
blue for interactive elements only; render structural accents (underlines, dividers) from the
neutral ramp.

### Minor

**Interaction states — table rows.** Rows have no hover state and the row-action icons have no focus
ring, so keyboard users can't see where they are [`projects-table-hover.png`]. *Fix:* add a subtle
`hover` background on rows and a visible `focus-visible` ring on every actionable control.

**Typography — empty state.** The empty-projects message uses a fourth body size that appears nowhere
else, breaking the scale [`empty-state.png`]. *Fix:* fold it into the existing caption size.

### Polish

**Motion — modal entrance.** The modal snaps in with no transition. *Fix:* a 200ms ease-out
fade-and-rise; gate it behind `prefers-reduced-motion`.

**Elevation — cards vs. modal.** Project cards and the modal use nearly the same shadow, so the modal
doesn't read as lifted above the page [`create-modal.png`]. *Fix:* lighten/flatten the card shadow
and deepen the modal's so elevation tracks the layering.

## Plan

**Quick wins (high impact, low effort) — do first:**

1. Add the loading + success feedback to the Create button (fixes the Blocker).
2. Make **New project** the only primary button; demote the other two (fixes the hierarchy Major).
3. Add row hover and focus-visible rings across interactive controls.

**Deeper changes:**

4. Audit every use of the brand blue and pull it back to interactive-only; introduce neutral
   structural accents (touches the whole app, so do it in one consistent pass).
5. Reconcile the type scale and the elevation scale into shared tokens so cards, modals, and text
   stop drifting per-component.

Want me to implement the quick wins now?
