---
name: code-review-to-subtask-translator
render_family: plan
description: Translate code-review findings and implementation notes into delivery-ready subtasks. Use when you need to convert review comments, defect observations, risk callouts, or change-plan notes into concrete implementation work with dependencies, ownership hints, and traceability back to the findings.
---

# Code Review To Subtask Translator

Turn review findings into actionable implementation work without losing the original risks and rationale.


Use this skill when a code review already surfaced problems or follow-up work and the next step is execution planning rather than another review pass.

Use `story-subtask-planner` when you are decomposing a delivery-ready story from acceptance logic or examples. Use this skill when the source material is primarily review feedback, implementation concerns, or change-plan notes.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- code-review findings, implementation notes, or equivalent review feedback

Optional inputs:

- the associated story, example map, acceptance criteria, or sequence notes
- explicit severity or priority labels
- architecture constraints or preferred delivery order
## Translate The Findings

Use this sequence:

1. Confirm the review source and the risky behaviors or defects it describes.
2. Normalize the findings into distinct issues with location, impact, and recommended intent.
3. Group related findings when they clearly belong to the same implementation slice.
4. Turn each finding or finding cluster into concrete subtasks with dependencies and validation work.
5. Record which findings should stay separate because they affect different layers, risks, or release timing.

Prefer implementation-oriented subtasks such as validation, persistence, interaction-flow, API, or test work over vague reminders like "fix review comments."

When a finding is too ambiguous to implement safely, create an explicit open question or spike instead of guessing.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Capture:

- source review findings
- normalized issues
- resulting subtasks
- dependency hints
- validation or testing follow-up
- assumptions and open questions
- traceability from findings to subtasks

## Quality Bar

Ensure the result:

- preserves the original review concern,
- produces work items implementers can act on immediately,
- separates real implementation work from ambiguity or discovery,
- and gives downstream planning skills clean traceability instead of raw review text.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
