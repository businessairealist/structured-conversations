---
name: product-elevator-pitch-writer
render_family: matrix
description: Build or update a product elevator pitch  using the classic seven-line structure and a rendered persona-column pitch canvas. Use when you need to draft product messaging from notes, upstream mapping artifacts, or explicit inputs and present it in a workshop-friendly format similar to the Product Elevator Pitch canvas.
---

# Product Elevator Pitch Writer

Build a structured product elevator pitch artifact rooted in the workspace.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- Product or concept name.
- At least one target audience or persona.
- A customer problem, need, or situation.
- A category or product framing.
- A core value statement.
## Structure The Pitch

Represent each persona pitch with the classic seven-line syntax:

1. `For`
2. `Who`
3. `The`
4. `Is/Are`
5. `That`
6. `Unlike`
7. `Our Product`

Then include the composed full elevator pitch sentence or paragraph for each persona.

Match the wording to the intended audience:

- Keep each line concrete and benefit-led.
- Prefer evidence-backed language from notes or upstream artifacts.
- When the audience is broad or inputs are thin, keep the draft concise rather than over-specific.

## Related Inputs And Downstream Use

Useful upstream sources:

- `artifacts/mapping/` journey maps, empathy maps, impact maps, and story maps
- `artifacts/foundation/` normalized problem statements or syntax decisions
- `inputs/notes/` and `intake/` narrative context

Common downstream skills:

- `elevator-pitch-to-epic-translator`
- `persona-pitch-adapter`
- `pitch-comparison-matrix-builder`

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

