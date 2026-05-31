---
name: story-subtask-planner
render_family: plan
description: Break a delivery-ready story into actionable subtasks. Use when you need to turn a story plus supporting specification detail into implementation work across frontend, backend, database, integration, testing, and DevOps while surfacing dependencies, handoffs, and unresolved technical questions.
---

# Story Subtask Planner

Turn a delivery-ready story into concrete team work without losing the story’s outcome.


Use this skill only after the story is ready enough for implementation planning. Reuse `invest-readiness-checker` and the shared `story_ready_for_subtasking` gate if readiness is still uncertain.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a selected story artifact
- supporting acceptance, example, or equivalent specification detail

Optional inputs:

- code-review notes
- sequence-diagram context
- architecture constraints or team ownership hints
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Try to locate the current or approved story and its supporting specification artifacts before asking the user to paste them.
- If multiple plausible stories exist, present a short user-facing picker based on topic, status, and recency.
- Show the resulting plan through its readable task surface and make dependencies and next actions explicit.

Do not decompose a story that clearly fails `story_ready_for_subtasking` without first recording that risk.

## Plan The Subtasks

Use this sequence:

1. Reconfirm the story goal and scope boundary.
2. Review implementation signals from examples, acceptance logic, code-review notes, or diagrams.
3. Break the work into functional subtasks across the actual delivery concerns involved.
4. Record dependencies, handoffs, and prerequisite sequencing.
5. Surface technical unknowns that should become spikes or explicit questions.

Prefer functional, outcome-oriented subtasks over team-role placeholders.

When the user wants a workshop artifact, organize the plan into the same four-part flow shown in the sample image:

- current code review
- code modification discussion and ideas
- sequence diagram or interaction flow
- implementation subtasks

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Capture:

- source story
- supporting specification artifacts
- subtasks
- dependencies and order
- handoffs
- unresolved technical questions
- traceability to upstream artifacts

## Quality Bar

Ensure the plan:

- is actionable for implementers,
- preserves the story outcome instead of collapsing into a task checklist detached from user value,
- makes dependencies explicit,
- and clearly separates known work from open questions or spikes.
