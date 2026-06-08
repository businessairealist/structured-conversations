---
name: invest-readiness-checker
render_family: matrix
description: Evaluate a drafted user story against the INVEST criteria and record rewrite guidance. Use when you need to assess whether a story is independent, negotiable, valuable, estimable, small, and testable before example mapping, slicing, or subtasking.
---

# INVEST Readiness Checker

Evaluate a story against INVEST, explain where it fails, and rewrite or recommend follow-up work when needed.


Use this skill after `user-story-drafter` or whenever a story is about to move into example mapping, splitting, or subtasking.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a selected story artifact or equivalent drafted story

Optional inputs:

- supporting examples, acceptance logic, or known constraints
- the intended downstream handoff such as example mapping or subtasking
## Run The Gate

Evaluate each criterion explicitly:

- Independent
- Negotiable
- Valuable
- Estimable
- Small
- Testable

Use this sequence:

1. Confirm the story and its immediate supporting context.
2. Score or label each INVEST criterion with evidence.
3. Explain the most important failure modes first.
4. Rewrite the story or propose the smallest repair that would improve readiness.
5. Record whether the story appears ready for `story_ready_for_example_mapping`, `story_ready_for_subtasking`, both, or neither.

Do not mark a story ready just because it sounds polished. Readiness depends on scope, testability, and downstream usefulness.

Stop and ask for clarification when the selected artifact is not actually a story or when multiple plausible story candidates remain unresolved.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Capture:

- evaluated story
- criterion-by-criterion findings
- rewrite guidance or revised story
- gate outcome for likely downstream handoffs
- assumptions
- open questions

Generate HTML only when the user wants a checklist or review table. If rendered, use a matrix-like presentation similar to the sample story-format board, with clear per-criterion pass/fail visibility.

## Quality Bar

Ensure the output:

- tells the team what must change, not just that the story is weak,
- preserves traceability to the evaluated story,
- distinguishes between rewrite, split, and spike decisions,
- and keeps the gate result visible for downstream skills.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
