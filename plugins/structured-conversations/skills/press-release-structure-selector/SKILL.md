---
name: press-release-structure-selector
render_family: board
description: Choose the best future press release structure . and a rendered option-comparison canvas. Use when you need to compare the three supported working-backwards press release structures, explain why one fits the product context best, and generate a starter scaffold for downstream writing.
---

# Press Release Structure Selector

Choose the best future press release option before drafting the full document.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- Product or concept name.
- Target audience or market.
- Problem or customer need.
- Planned solution or product promise.
## Selection Goal

Compare the three supported working-backwards press release patterns and recommend one.

The output must include:

- the three option structures
- the recommended option
- the reason it fits the request
- a starter scaffold the writer can consume next

## Related Inputs And Downstream Use

Useful upstream sources:

- `artifacts/foundation/` normalized problem statements
- `artifacts/mapping/` empathy, journey, impact, and story artifacts
- `artifacts/vision/` elevator pitches and prior narrative drafts
- `inputs/notes/` and `intake/` product framing

Common downstream skill:

- `future-press-release-writer`

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
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

