---
name: empathy-map-builder
render_family: board
description: Build or update an empathy map from customer evidence. Use when you need to turn notes, quotes, tickets, screenshots, observations, interview snippets, or upstream discovery artifacts into a structured empathy map for a specific actor/persona across what they see, hear, say, do, think, and feel.
---

# Empathy Map Builder

Build an empathy map as a board artifact rooted in evidence, not opinion.

Render the finished artifact in the classic empathy-mapping poster format when possible: instructional panel on the left, `who` and `goal` at the top, `hear` on the left, `see` on the right, `say` on the lower right, `do` across the bottom, and a central think/feel area split into pains and gains.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- Target actor or persona.
- Research evidence such as notes, quotes, observations, tickets, screenshots, support logs, or interview snippets.

Optional inputs:

- Persona constraints.
- Segment tags.
- Source confidence levels.
- Request to create a fresh map or update an existing one.
## Structure the Map

Organize the artifact around one clearly named actor. Build sections from evidence:

- `who`: actor name, segment, context, goal, and constraints
- `see`: environment, interfaces, competing signals, blockers, and surrounding context
- `hear`: things the actor hears from teammates, managers, peers, support, or the market
- `say`: direct quotes, paraphrased statements, and recurring claims
- `do`: observable actions, workarounds, habits, and decision patterns
- `think`: likely beliefs, questions, tradeoffs, and mental models
- `feel`: emotions, anxieties, motivations, and confidence signals

For each card or statement:

- Prefer evidence-backed wording.
- Attach source references when possible.
- Mark inference clearly when it is not directly stated.
- Keep stable card or node IDs so partial updates do not scramble unchanged content.

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

