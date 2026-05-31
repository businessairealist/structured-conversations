---
name: future-press-release-writer
render_family: form
description: Build or update a future press release . and one of the three supported working-backwards press release structures. Use when you need to write a future-state launch announcement, preserve assumptions and open questions, and render the result as a readable HTML document.
---

# Future Press Release Writer

Write a future-state press release that describes customer success as if launch has already happened.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- Product or concept name.
- Target audience or market.
- Problem being solved.
- Planned solution or product promise.
## Writing Goal

Write the press release as if the product already exists and delivers value.

The output must:

- use one of the three supported structures
- name the audience and problem clearly
- make the solution concrete enough to discuss with a development team
- preserve assumptions and open questions instead of pretending certainty

## Related Inputs And Downstream Use

Useful upstream sources:

- - - `artifacts/mapping/` discovery artifacts
- `inputs/notes/` and `intake/`

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

