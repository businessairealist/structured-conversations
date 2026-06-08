---
name: living-documentation-builder
render_family: form
description: Organize validated scenarios into executable living documentation. Use when you need to turn Gherkin scenarios and their upstream traceability into version-controlled feature bundles, readable reports, and documentation that remains aligned with system behavior over time.
---

# Living Documentation Builder

Turn validated scenarios into a durable documentation package that teams can read, review, and maintain.


Use this skill after `gherkin-scenario-writer` or when a project already contains compatible `.feature` exports and linked scenario artifacts.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- validated scenarios or compatible Gherkin scenario artifacts

Optional inputs:

- preferred feature grouping
- report sections or audience emphasis
- linked evidence or release/version context
## Build The Documentation Bundle

Use this sequence:

1. Select the latest compatible scenario source.
2. Confirm the scenarios are stable enough to document rather than still in dispute.
3. Group scenarios into coherent feature-level documentation units.
4. Preserve links to upstream stories, examples, assumptions, and open questions.
5. Generate readable summaries without replacing the canonical scenario content.

Treat the scenario artifact as the behavioral source of truth. Documentation is a maintained derivative, not a separate truth.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. One or more `.feature` files or documentation bundles organized by feature area
2. A structured markdown index linking features to their source artifacts

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-living-docs.md`).

## Update Integrity

When updating existing documentation:

- preserve stable feature grouping where possible,
- update the structured output first,
- regenerate only affected derivatives,
- and carry forward upstream traceability and stale-state signals.

If upstream scenarios changed materially, record whether the documentation supersedes an older artifact or whether downstream recomputation is required.

## Quality Bar

Ensure the documentation:

- stays traceable to executable scenarios,
- remains readable for humans,
- avoids diverging from the canonical behavioral artifacts,
- and makes change impact visible instead of hiding it.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
