---
name: data-driven-decision-framer
render_family: form
description: Frame pre-committed decisions for different evidence outcomes. Use when you need a canonical decision artifact that turns experiment results into clear next actions.
---

# Data Driven Decision Framer

Create a reusable decision artifact that makes pass, mixed, and fail outcomes actionable before the experiment runs.


Use this skill after hypotheses and experiment signals are defined, or anytime a team is collecting data without clarity on what decision the data is meant to inform.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one decision question
- one experiment, evidence source, or framing signal

Optional inputs:

- pass, mixed, and fail conditions
- decisions for each outcome path
- confidence or risk notes
- owner or review cadence
## Frame Decisions

Use this sequence:

1. Confirm the decision that needs to be made.
2. Capture the signals or evidence that will inform it.
3. Define what pass, mixed, and fail mean in practical terms.
4. Record the corresponding action for each path before results arrive.

Prefer pre-commitment over vague “we’ll decide later” language.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the artifact:

- makes the decision question explicit,
- maps likely evidence states to concrete actions,
- keeps risk and uncertainty visible,
- and stays easy to reuse from an experiment artifact.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
