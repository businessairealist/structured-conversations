---
name: future-press-release-template-generator
render_family: form
description: Generate reusable future-press-release templates across the supported working-backwards structures. Use when you need a canonical blank press-release artifact before a specific launch narrative is written.
---

# Future Press Release Template Generator

Create a reusable future press release template artifact based on one of the supported structures.


Use this skill when a team wants a blank working-backwards press-release structure before drafting a concrete narrative.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one template title or context

Optional inputs:

- preferred structure option
- section prompt overrides
## Generate The Template

Use this sequence:

1. Choose one of the supported structure options.
2. Preserve the section order for that option.
3. Fill each section with a prompt rather than finished launch copy.
4. Keep the template easy to convert into a future press release later.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the template:

- matches one supported structure exactly,
- keeps prompts customer-facing and future-state,
- stays reusable across concepts,
- and remains compatible with `future-press-release-writer`.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
