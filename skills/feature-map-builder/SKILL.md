---
name: feature-map-builder
render_family: board
description: "Build a feature map from a feature slice, actors, rules, examples, steps, outcomes, and open questions. Use when you need a structured discovery artifact while acceptance criteria are still forming."
---

# Feature Map Builder

Build a feature map artifact from a feature slice, actors, rules, examples, steps, outcomes, and open questions.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

## Use When

- the user wants to break a feature into a structured discovery artifact
- acceptance criteria are still forming and the team needs a better requirements picture
- downstream skills need a feature-oriented source artifact

## Inputs

- feature name
- optional actors, rules, examples, steps, outcomes, and questions
- optional source notes or artifact paths

## Process

1. collect the feature slice and supporting context
2. separate actors, rules, examples, steps, and outcomes into clear lanes
3. preserve unresolved questions
4. emit a canonical feature-map output package

## Outputs

- the working directory<slug>/the structured output
- the working directory<slug>/the readable summary
- HTML render and manifest files for downstream use

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Try to locate the best existing feature slice, source notes, or upstream artifact before asking for content.
- If the project contains multiple plausible feature artifacts, present a short choice list instead of raw paths.
- Default the user review surface to the readable HTML or Markdown view.
- After generation, tell the user to review actors, rules, examples, and open questions, then recommend the most likely next step.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

