---
name: story-splitting-method-selector
render_family: tree
description: Choose the best method for splitting an oversized story. Use when you need to decide between approaches such as hamburger slicing, SPIDR, decision-tree questioning, or a spike before producing smaller vertical slices.
---

# Story Splitting Method Selector

Choose the splitting technique that best matches the story’s source of complexity, then explain why.


Use this skill before `user-story-splitter` when the team knows the story is too large but does not yet know how to break it down.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- an oversized or at-risk story

Optional inputs:

- example-map detail
- known uncertainty or technical unknowns
- preferred slicing style
## Select The Method

Compare these families:

- hamburger method for progressive quality layers within one vertical path
- SPIDR when splits emerge from rules, data, interfaces, paths, or spikes
- question-driven decision-tree guidance when the issue is not yet well classified
- spike-first when the story contains dominant uncertainty rather than dominant scope

Use this sequence:

1. Identify why the story feels too large or risky.
2. Distinguish scope complexity from uncertainty.
3. Select the best-fit splitting method.
4. Record why the competing methods are less suitable.
5. Suggest the likely next skill: `user-story-splitter` or `spike-writer`.

Prefer methods that preserve vertical value and avoid technical-layer splits by default.

Stop and ask for clarification when the story is missing the behavior being split, or when the apparent problem is really an upstream ambiguity that should be resolved before slicing.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact as an interactive tree (collapsible parent-child hierarchy with branching). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

Render HTML when the team wants a workshop aid. When rendered, structure it like the sample splitting board: original story panel, method comparison area, and a clear recommendation path.

## Quality Bar

Ensure the output:

- distinguishes between splitting and spiking,
- explains the method in practical terms,
- preserves the original story intent,
- and gives `user-story-splitter` a clear starting point.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
