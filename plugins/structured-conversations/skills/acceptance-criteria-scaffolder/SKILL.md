---
name: acceptance-criteria-scaffolder
render_family: matrix
description: Convert a drafted story plus mapped rules or examples into observable acceptance criteria. Use when you need to produce testable acceptance criteria before implementation, example mapping, or Gherkin writing.
---

# Acceptance Criteria Scaffolder

Turn a story and its supporting rules into acceptance criteria that describe observable outcomes instead of implementation steps.


Use this skill when the story is understood well enough to describe expected behavior, validation, and business rules, but the team still needs a concrete acceptance layer before delivery work starts.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a drafted story or equivalent requirement statement

Optional inputs:

- feature-map detail
- example-map rules or examples
- known business thresholds, evidence rules, or escalation paths
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best available story, feature map, or example map before asking the user to paste context again.
- If more than one plausible upstream artifact matches, present a short choice using title, topic, and recency.
- Default the user to reviewing the readable summary or the HTML render, not raw runtime metadata.
- After generation, tell the user what to review and suggest example mapping as the recommended next step.

## Scaffold The Criteria

Use this sequence:

1. Confirm the story and its main customer or business outcome.
2. Identify the happy path, validation path, and key business-rule outcomes.
3. Phrase the criteria as observable behavior the team can test.
4. Preserve critical routing, threshold, or evidence rules when they materially affect the outcome.
5. Record open questions instead of inventing unclear rules.

Prefer criteria that a tester, reviewer, or stakeholder could verify from system behavior.

Avoid:

- implementation-only language
- hidden business rules
- vague quality statements with no visible outcome

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the criteria:

- describe observable behavior,
- preserve the business outcome of the story,
- surface key blocking or exception paths,
- and give downstream example-mapping, Gherkin, and delivery skills a reliable contract.

Tell the user to review:

- whether the happy path is testable,
- whether blocking rules are complete,
- and whether any edge case should be turned into an example or scenario next.
