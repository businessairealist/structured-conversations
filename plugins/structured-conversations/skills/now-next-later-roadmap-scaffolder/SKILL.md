---
name: now-next-later-roadmap-scaffolder
render_family: board
description: Build or update a goal-oriented now-next-later roadmap from desired outcomes, initiatives, evidence, and customer needs. Use when you need a poster-style roadmap board with Now, Next, Later, and product outcome columns rather than a date-driven feature list.
---

# Now Next Later Roadmap Scaffolder

Build a goal-oriented roadmap from evidence rooted in evidence.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- One clear product, business, or customer goal.
## Structure The Roadmap

Use horizon-based prioritization, not date theater.

At minimum capture:

- roadmap title and revision date
- one goal row
- initiatives grouped into Now, Next, and Later
- explicit product outcomes and customer-needs outcomes
- why, what, and evidence notes when available
- assumptions, dependencies, and open questions

Place the highest-confidence, highest-leverage work in Now. Use Next and Later for lower-confidence or later-sequenced bets, and keep outcome linkage visible in every horizon.

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

