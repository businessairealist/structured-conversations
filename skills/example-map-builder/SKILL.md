---
name: example-map-builder
render_family: board
description: Build an example map from a story and its acceptance criteria. Use when you need to connect rules to concrete examples and open questions before Gherkin writing or implementation.
---

# Example Map Builder

Turn a story and its acceptance criteria into an example map with rules, examples, and unresolved questions.


Use this skill after `acceptance-criteria-scaffolder` or whenever the team is ready to pressure-test the story with concrete examples instead of only abstract rules.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a drafted story or equivalent requirement

Optional inputs:

- acceptance criteria
- feature rules
- known policy thresholds or exception cases
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the latest compatible acceptance criteria and story before asking the user for more input.
- If there are several plausible maps or stories, offer a short picker instead of making the user remember paths.
- Direct the user to review the readable map output first and keep runtime metadata in the background.
- After generation, recommend Gherkin scenario writing unless the map still has blocking questions.

## Build The Example Map

Use this sequence:

1. Confirm the story and the main rule set.
2. Convert material rules into concrete examples with Given/When/Then structure.
3. Add negative or blocking examples when the rules imply validation or failure handling.
4. Record unresolved questions that still block confident implementation.

Keep rules, examples, and questions distinct so downstream scenario-writing work stays clean.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

Ensure the map:

- connects each rule to at least one concrete example,
- includes meaningful validation or exception examples when needed,
- preserves traceability to the source story and acceptance criteria,
- and gives `gherkin-scenario-writer` a clean next step.

Tell the user to review:

- whether each rule has enough concrete examples,
- whether negative cases are realistic,
- and whether any question still blocks scenario writing.
