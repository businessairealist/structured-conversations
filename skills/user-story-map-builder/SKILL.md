---
name: user-story-map-builder
render_family: board
description: Build or update a classic user story map from actor, workflow, and delivery evidence. Use when you need a poster-style map with a guide panel, user and goal summary, activity/task/story layers, and release slices.
---

# User Story Map Builder

Build a user story map from evidence rooted in evidence.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- Target actor or persona.
- Primary user goal.
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Try to locate the best existing actor, goal, and supporting evidence before asking the user to restate them.
- If one relevant current artifact or note set is clearly the right input, use it and say so.
- If more than one plausible map or evidence bundle exists, present a short user-facing choice instead of requiring a path.
- Ask for uploaded or pasted content only when the project does not contain a safe match.
- After generation, direct the user to review the map in its readable surface and suggest the next likely step.

## Structure The Map

Organize the artifact around one clearly named persona and one user goal.

At minimum capture:

- backbone activities in deterministic order
- user tasks under each activity
- user stories under each activity
- release slices or walking-skeleton grouping
- assumptions and open questions where the delivery structure is still uncertain

Prefer evidence-backed wording. Keep weakly supported stories explicit as draft backlog candidates.

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

