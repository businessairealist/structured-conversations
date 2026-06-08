---
name: initiative-to-keyresult-aligner
render_family: matrix
description: Align candidate initiatives against measurable key results. Use when you need a clear explanation of which initiatives are expected to move which results before drafting an OKRI record or OKR board.
---

# Initiative To Keyresult Aligner

Create a reusable alignment artifact that shows which initiatives plausibly move each key result.


Use this skill when a team has ideas for work but the measurement logic is vague, or when existing OKRs need stronger initiative linkage before planning or review.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one objective or framing goal
- one or more measurable key results
- one or more candidate initiatives

Optional inputs:

- evidence
- assumptions
- dependencies
- expected mechanism or rationale
## Build Alignment

Use this sequence:

1. Confirm the objective and measurable key results.
2. Review each initiative for explicit linkage to the key results it is meant to move.
3. Mark the linkage as strong, partial, or weak.
4. Keep unsupported initiatives visible as assumptions or open questions.

Avoid vague “supports growth” language when a more concrete movement claim can be stated.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Generate Mermaid when the alignment can be represented faithfully.

## Quality Bar

Ensure the artifact:

- ties work to measurable results,
- exposes weak or speculative initiative linkage,
- keeps evidence and assumptions visible,
- and stays usable as input to `okri-builder`.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
