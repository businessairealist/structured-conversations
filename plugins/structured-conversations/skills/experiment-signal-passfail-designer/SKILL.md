---
name: experiment-signal-passfail-designer
render_family: matrix
description: Define experiment signals plus pass, mixed, and fail thresholds. Use when you need a canonical measurement artifact that makes experiment evaluation consistent and reviewable.
---

# Experiment Signal Passfail Designer

Create a reusable measurement artifact that spells out what to observe and what counts as success, ambiguity, or failure.


Use this skill when a team has an experiment idea but has not yet made the evaluation logic concrete enough for review.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one experiment
- one desired outcome

Optional inputs:

- signals
- baselines
- pass, mixed, and fail thresholds
- sample or timing notes
- data-quality risks
## Design Evaluation Logic

Use this sequence:

1. Confirm the experiment and the desired outcome.
2. Name the signals that best indicate movement.
3. Define what pass, mixed, and fail mean for each important signal.
4. Record constraints that could weaken interpretation.

Prefer thresholds and concrete comparisons over fuzzy “looks good” judgments.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the artifact:

- clearly defines evaluation signals,
- distinguishes pass from mixed and fail,
- makes interpretation risks explicit,
- and stays easy to reuse in a decision artifact.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
