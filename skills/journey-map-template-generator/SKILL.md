---
name: journey-map-template-generator
render_family: board
description: Generate a reusable customer-journey map template. Use when you need a stage-based journey canvas for workshops before project evidence is added.
---

# Journey Map Template Generator

Generate a reusable customer-journey board template with standard stage and row structure.


Use this skill when the team needs a blank or lightly example-filled journey canvas. Use `customer-journey-map-facilitator` when the artifact should already guide a live workshop.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- placeholder persona or persona label

Optional inputs:

- custom stages
- whether to include example rows
- artifact slug override
## Generate The Template

Create a stage-based journey board with reusable rows for the main journey dimensions.

Use example rows only when the user wants a lightly pre-filled template.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

Ensure the template:

- remains stage-based and persona-centered,
- distinguishes reusable prompts from project evidence,
- supports workshop and analysis flows,
- and aligns with the journey builder and facilitator skills.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
