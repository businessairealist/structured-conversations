---
name: epic-hypothesis-template-generator
render_family: form
description: Generate a reusable epic-hypothesis statement template. Use when you need a canonical blank statement structure before a specific epic is fully drafted.
---

# Epic Hypothesis Template Generator

Create a reusable template artifact for epic hypothesis statements.


Use this skill when a team wants the standard epic hypothesis format available as a canonical template before filling in a concrete epic.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one title or context for the template

Optional inputs:

- prompt text for epic name, owner, description, outcomes, OKR, indicators, and NFR
## Generate The Template

Use this sequence:

1. Preserve the standard epic-hypothesis fields.
2. Keep each field phrased as a fill-in prompt, not finished content.
3. Make the template easy to convert into a drafted epic later.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the template:

- preserves the full epic hypothesis structure,
- uses prompts that encourage outcome-driven thinking,
- stays reusable across epics,
- and remains compatible with `outcome-driven-epic-writer`.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
