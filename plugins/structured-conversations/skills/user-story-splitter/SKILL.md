---
name: user-story-splitter
render_family: board
description: Split oversized user stories into smaller vertical slices. Use when you need to apply cake slicing, hamburger quality levels, SPIDR dimensions, or decision-tree guidance to produce smaller delivery-ready stories while preserving value and traceability to the original story.
---

# User Story Splitter

Break a large story into smaller vertical slices without losing the user outcome.


Use `story-splitting-method-selector` first when the splitting approach is not yet clear. Use `spike-writer` instead when uncertainty dominates scope.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a story that is too large, too risky, or too broad

Optional inputs:

- selected splitting method
- example-map detail, acceptance logic, or release constraints
- target number of slices or preferred release order
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the current story and supporting specification artifacts before asking the user to restate them.
- If more than one candidate story exists, present a short picker with status and recency.
- Keep the review surface on the split plan itself rather than exposing backend folder structure.
- After generation, recommend subtask planning unless the slices still contain major uncertainty.

## Split The Story

Use this sequence:

1. Confirm the original story and why it needs splitting.
2. Select or honor the split method.
3. Generate smaller vertical slices that each preserve a coherent user outcome.
4. Keep shared assumptions or prerequisites visible instead of duplicating hidden scope.
5. Record ordering, dependency hints, and candidate release groupings.
6. Flag any slice that should really become a spike.

Avoid anti-patterns:

- pure frontend/backend/database splits
- slices that produce no user-visible or behavior-visible value
- splitting by task ownership alone
- rewriting the story so heavily that traceability to the original story disappears

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

Capture:

- original story
- chosen split method
- resulting slices
- rationale per slice
- ordering or release hints
- assumptions and open questions
- traceability to the original story and supporting artifacts

When rendered, mirror the sample splitting canvas: original story on the left, method-specific split areas in the center, and decision-tree or follow-up guidance on the right.

## Quality Bar

Ensure the result:

- preserves user value in each slice,
- makes downstream estimation and implementation easier,
- keeps unknowns explicit,
- and gives `story-subtask-planner` smaller, cleaner units to work from.

Tell the user to review:

- whether each slice stands on its own,
- which slice should go first,
- and whether any slice should really be a spike instead.
