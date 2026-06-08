---
name: spike-writer
render_family: form
description: Frame delivery uncertainty as a focused, time-boxed spike. Use when you need to turn a risky story, unresolved integration question, or ambiguous implementation path into a learning-oriented spike with a goal, constraints, acceptance criteria, and a follow-on delivery recommendation.
---

# Spike Writer

Turn uncertainty into a bounded spike artifact that the team can execute and learn from.


Use this skill when the right next step is to learn, compare, or de-risk rather than deliver production behavior immediately.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- the question, risk, or uncertainty that blocks confident delivery

Optional inputs:

- related story or split artifact
- known time-box
- desired learning output or comparison criteria
## Write The Spike

Use this sequence:

1. Identify the exact uncertainty.
2. Convert it into a learning goal and bounded scope.
3. Define the time-box and expected deliverables.
4. State acceptance criteria for the spike itself.
5. Record how the findings should flow back into implementation work.

Good spikes answer a question. They do not become disguised build tasks.

Stop and ask for clarification when the request is really a normal implementation story or when the uncertainty is too vague to bound safely.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Capture:

- source uncertainty
- learning goal
- time-box
- scope boundaries
- spike acceptance criteria
- expected outputs
- next-step recommendation for delivery work

Render HTML only when the user wants a brief or team-ready handout.

## Quality Bar

Ensure the spike:

- is genuinely learning-oriented,
- is small enough to finish,
- produces a clear decision or follow-on recommendation,
- and preserves lineage back to the story or implementation risk that triggered it.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
