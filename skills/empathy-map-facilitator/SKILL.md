---
name: empathy-map-facilitator
render_family: board
description: Generate a workshop-ready empathy-map facilitation board. Use when you need a live-session artifact for gathering observations, quotes, actions, thoughts, and feelings collaboratively around one actor.
---

# Empathy Map Facilitator

Create a facilitation board for running an empathy-mapping workshop around a single actor.


Use this skill when the team wants to gather or structure evidence collaboratively. Use `empathy-map-builder` when the content should be built directly from evidence instead of a workshop format.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- target actor or persona

Optional inputs:

- workshop participants
- a session goal
- segment or context label
## Facilitate The Workshop

Use this sequence:

1. Restate the actor and session goal.
2. Capture direct observations and quotes before interpretations.
3. Keep actions, thoughts, and feelings distinct.
4. Mark inference explicitly when evidence is weak.
5. End with tensions, open questions, and next evidence gaps.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

Ensure the workshop board:

- keeps evidence ahead of interpretation,
- stays focused on one actor,
- makes tensions and evidence gaps explicit,
- and remains ready for downstream insight extraction.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
