---
name: okr-mapping-template-generator
render_family: board
description: Generate a reusable OKR mapping template. Use when you need a canonical board scaffold for objective, key-result, and initiative mapping before a specific OKR set is fully populated.
---

# OKR Mapping Template Generator

Create a reusable template artifact for OKR mapping and workshop facilitation.


Use this skill when a team needs a repeatable OKR board structure before filling in a specific objective, key results, and initiatives.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one title or context for the template

Optional inputs:

- objective prompt
- key result prompts
- initiative prompts
- alignment notes
## Generate The Template

Use this sequence:

1. Define the objective zone.
2. Provide reusable prompts for measurable key results.
3. Include initiative prompts that keep work visibly subordinate to outcomes.
4. Leave the structure ready for later conversion into a populated OKR map or OKRI.

Prefer prompts that reinforce measurable outcomes over activity lists.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

Ensure the template:

- keeps objective, key result, and initiative roles distinct,
- encourages measurable key results,
- stays reusable across teams,
- and remains compatible with the OKR map and OKRI skills.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
