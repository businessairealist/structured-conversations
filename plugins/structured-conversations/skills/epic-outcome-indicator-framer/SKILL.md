---
name: epic-outcome-indicator-framer
render_family: form
description: Frame business outcomes, product OKRs, and leading indicators for an epic. Use when you need the measurable outcome layer of an epic clarified before or during hypothesis drafting.
---

# Epic Outcome Indicator Framer

Create a reusable artifact that connects an epic to business outcomes, product OKRs, and leading indicators.


Use this skill when an epic idea exists but its measurable success logic is still vague.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one epic name or epic context

Optional inputs:

- business outcomes
- product OKR
- leading indicators
- evidence notes
- risks or assumptions
## Frame The Outcome Logic

Use this sequence:

1. Confirm the epic context.
2. State the measurable business outcomes the epic should influence.
3. Identify the most relevant product OKR.
4. Name leading indicators that would show early movement.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the artifact:

- keeps outcomes measurable,
- separates business outcomes from leading indicators,
- gives the epic a clear OKR connection,
- and stays compatible with `outcome-driven-epic-writer`.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
