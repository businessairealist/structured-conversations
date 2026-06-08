---
name: pitch-comparison-matrix-builder
render_family: matrix
description: Create a side-by-side pitch comparison matrix to test resonance across target users. Use when you need to compare multiple complete pitch variants or messaging approaches in one artifact.
---

# Pitch Comparison Matrix Builder

Create a side-by-side comparison matrix for multiple pitch variants.


Use this skill when the team has multiple finished or semi-finished pitch variants and wants to compare wording, emphasis, or persona resonance in one place.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- two or more pitch variants

Optional inputs:

- comparison labels
- evaluation notes
- audience or persona context
## Build The Matrix

Use this sequence:

1. Normalize each pitch into the same row structure.
2. Preserve the variant label for each column.
3. Keep the final pitch statement visible for easy comparison.
4. Record any evaluation notes or open questions instead of forcing a winner.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the matrix:

- compares like with like across variants,
- keeps labels and audience context visible,
- makes differences in wording and emphasis easy to scan,
- and remains useful for pitch-selection discussions.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
