---
name: goal-oriented-roadmap-template-generator
render_family: board
description: Generate a reusable goal-oriented roadmap template. Use when you need a blank Now/Next/Later canvas with outcome and customer-needs structure before project-specific bets are added.
---

# Goal Oriented Roadmap Template Generator

Generate a reusable goal-oriented roadmap board template with horizon and outcome structure.


Use this skill when the team needs a reusable canvas. Use `goal-oriented-roadmap-builder` when the roadmap should already contain real bets, outcomes, and evidence.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- roadmap title or theme

Optional inputs:

- whether to include example cards
- a placeholder goal
## Generate The Template

Create a board with:

- title area
- goal area
- Now, Next, and Later horizons
- outcomes panel
- customer-needs panel

Use example cards only when the user wants a lightly pre-filled template.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

Ensure the template:

- remains reusable,
- makes horizon and outcome structure obvious,
- distinguishes prompts from real strategy content,
- and aligns with the roadmap builder and scaffolder skills.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
