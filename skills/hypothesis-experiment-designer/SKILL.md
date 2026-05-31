---
name: hypothesis-experiment-designer
render_family: form
description: Turn assumptions or early hypotheses into the smallest useful experiments with measurable signals, pass/fail rules, and next decisions. Use when you need a structured experiment design that can slot into a hypothesis tree or evidence-driven roadmap conversation.
---

# Hypothesis Experiment Designer

Design experiments for candidate hypotheses as a canonical strategy artifact.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- At least one hypothesis or assumption to test.
## Structure The Experiment Design

Make every experiment decision-ready.

At minimum capture:

- hypothesis statement
- experiment description
- target audience or sample
- desired outcome
- measurable signals
- pass/fail criteria
- cost, time, or scope constraints
- interpretation logic and next decision
- assumptions and open questions

Prefer one experiment per critical uncertainty. If the experiment is too large, reduce scope until the team can actually run it.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

