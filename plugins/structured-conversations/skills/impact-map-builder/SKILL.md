---
name: impact-map-builder
render_family: board
description: Build or update an impact map from a business goal, known actors, and behavior-change hypotheses. Use when you need to connect an outcome to actors, impacts, and deliverables so teams can identify the highest-leverage branches, expose gaps, and prepare downstream planning artifacts.
---

# Impact Map Builder

Build an impact map from evidence that links a business outcome to actors, impact hypotheses, and candidate deliverables.

Render the finished artifact in the classic impact-mapping poster format when possible: instructional panel on the left and five aligned columns for `WHY`, `WHO`, `HOW`, `WHAT`, and `VIA`.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- Business goal.
- Known actors.
- Behavior-change hypotheses or customer insights.
## Load The Impact Mapping References

Load the impact-map schema and the outcome wording guidance before synthesizing the artifact.

Use the intended builder entrypoint and shared workspace helpers:

- Shared helpers:

Use supporting skills when the wording or branch framing needs help:

- `verb-noun-rewriter`
- `syntax-pattern-selector`

## Structure The Map

Organize the artifact around a single outcome statement and branch outward through actors, impacts, and deliverables.

At minimum, capture:

- `goal`: the business outcome or change to achieve
- `actors`: the people, systems, or groups whose behavior matters
- `impacts`: the behavior changes or signals expected from each actor
- `deliverables`: candidate interventions, bets, or capabilities that could create the impact
- `via`: user stories or hypotheses that break the deliverables into smaller testable chunks

For each branch:

- prefer outcome-oriented wording over task lists,
- distinguish actor behavior from deliverable ideas,
- keep `via` items smaller and more executable than the `what` deliverables,
- keep success metrics or evidence links close to the branch when available,
- mark inferred impacts clearly when they are not directly evidenced,
- record gaps instead of fabricating certainty.

## Highlight Highest-Leverage Branches

The finished artifact should make it easy to spot:

- likely highest-leverage branches,
- weak assumptions or unsupported links,
- missing actors,
- missing impact hypotheses,
- over-specified deliverables that are not tied to measurable behavior change.


## Related Skills

Use these adjacent skills when the request is not pure impact-map building:

- `impact-map-facilitator` for workshop-led branching and group refinement.
- `impact-to-story-translator` when mapped branches should become stories or next-step backlog seeds.
- `empathy-to-action-translator` when empathy outputs need to be converted into action-oriented inputs before impact mapping.

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
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

