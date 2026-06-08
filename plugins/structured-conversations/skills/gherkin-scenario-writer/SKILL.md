---
name: gherkin-scenario-writer
render_family: scenario
description: Convert stories, rules, and examples into executable-style Gherkin scenarios. Use when you need to turn example maps, rule/example artifacts, or clarified stories into precise Given-When-Then scenarios for collaboration, testing, and automation.
---

# Gherkin Scenario Writer

Write scenarios that reflect the agreed rules and examples, not improvised behavior.


Use this skill after example mapping or equivalent rule-and-example clarification. Prefer `example_map_ready_for_gherkin` before writing large scenario sets.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- example-map detail, rule/example artifact, or equivalent acceptance logic

Optional inputs:

- linked story context
- feature grouping preferences
- automation tags, naming conventions, or background steps
## Write The Scenarios

Use this sequence:

1. Confirm the scenario source artifact and its linked story context.
2. Check whether `example_map_ready_for_gherkin` appears to pass.
3. Convert clear rules and examples into scenarios with stable titles.
4. Use `Given`, `When`, and `Then` only for meaningful preconditions, actions, and observable outcomes.
5. Preserve open questions instead of encoding guesses as scenario steps.

Prefer multiple focused scenarios over one giant scenario with many branches.

Stop and ask for clarification when the example set is too incomplete, contradictory, or ambiguous to encode safely.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. One or more `.feature` files containing the Gherkin scenarios
2. A structured markdown summary linking scenarios to their source rules and examples

Name files using kebab-case descriptive slugs (e.g., `checkout-login-scenarios.feature`).

## Quality Bar

Ensure the scenarios:

- reflect agreed behavior rather than implementation guesses,
- are readable by product, test, and engineering collaborators,
- preserve traceability to examples and rules,
- and are structured so `living-documentation-builder` can reuse them cleanly.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
