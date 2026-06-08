---
name: persona-pitch-adapter
render_family: matrix
description: Adapt one pitch structure across multiple personas or audience segments side by side. Use when you need persona-specific pitch variants derived from one core product framing.
---

# Persona Pitch Adapter

Create persona-adapted pitch variants from one core product framing.


Use this skill when the core product pitch is stable but the audience framing needs to shift across personas without rewriting the whole narrative from scratch.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one product or offer name
- one core pitch framing
- two or more personas or audience segments

Optional inputs:

- persona-specific problem language
- persona-specific value emphasis
- alternative or differentiator notes
## Adapt The Pitch

Use this sequence:

1. Preserve one shared product framing.
2. Tailor the audience, problem, and value rows for each persona.
3. Keep the final pitch statements easy to compare side by side.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the output:

- keeps one clear shared pitch structure,
- makes persona-level differences visible,
- avoids drifting into unrelated messaging by persona,
- and remains compatible with pitch-comparison work.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
