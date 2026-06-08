---
name: journey-to-priority-translator
render_family: matrix
description: Translate a completed customer journey map into prioritized improvement opportunities. Use when you need to turn friction-heavy journey evidence into a ranked set of candidate priorities.
---

# Journey To Priority Translator

Turn journey-map friction into prioritized improvement opportunities.


Use this skill after `customer-journey-map-builder`, `customer-journey-map-facilitator`, or `journey-friction-analyzer` when the team is ready to move from understanding the journey to choosing what to improve first.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a completed customer-journey-map artifact

Optional inputs:

- specific journey artifact id or slug
- context about whether the result should feed backlog shaping or broader discovery
## Translate The Journey

Use this sequence:

1. Load the journey stages and preserve the strongest friction evidence.
2. Rank the highest-friction stages or moments.
3. Translate those moments into prioritized improvement opportunities.
4. Keep clear traceability from each priority candidate back to the journey evidence.
5. Record open questions when the improvement candidate still needs validation.

Treat the output as ranked opportunity candidates, not fully committed backlog items.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the output:

- stays anchored in journey evidence,
- prioritizes the most meaningful friction first,
- makes the candidate nature of the priorities explicit,
- and provides a clean bridge into backlog or roadmap shaping.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
