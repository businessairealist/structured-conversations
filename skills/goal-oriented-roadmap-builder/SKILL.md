---
name: goal-oriented-roadmap-builder
render_family: board
description: Build a goal-oriented roadmap artifact from a strategic goal, outcomes, and candidate bets. Use when you need a Now/Next/Later roadmap that keeps customer and business outcomes visible instead of defaulting to date-driven feature lists.
---

# Goal Oriented Roadmap Builder

Build a roadmap anchored in a strategic goal, desired outcomes, and horizon-based initiative placement.


Use this skill when the team already has enough strategic context to place work into horizons and wants a reusable canonical roadmap artifact. Use `now-next-later-roadmap-scaffolder` when the task is closer to a guided poster-style workshop flow.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one strategic goal
- candidate bets or initiatives
- desired outcomes

Optional inputs:

- customer needs
- evidence or confidence notes
- dependencies
- last revised date
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Try to locate the best existing strategy inputs before asking the user to re-enter goals, outcomes, or candidate bets.
- Prefer current or approved roadmap-related artifacts when the project already contains them.
- If more than one roadmap candidate is plausible, present a short user-facing choice list.
- Show the roadmap through its readable review surface and recommend the next likely strategic step after generation.

## Build The Roadmap

Use this sequence:

1. Confirm the strategic goal and the outcomes that matter.
2. Gather candidate bets and place them into Now, Next, or Later based on confidence and sequencing.
3. Keep customer-needs and outcome linkage visible.
4. Record lower-confidence bets or weak evidence as open questions instead of overcommitting.

Prefer horizon logic over dates. The roadmap should explain why work belongs in each horizon, not just when it happens.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

Generate Mermaid only when the roadmap can be represented faithfully.

## Quality Bar

Ensure the roadmap:

- stays outcome-first,
- keeps Now, Next, and Later placement defensible,
- makes customer-needs linkage visible,
- and leaves lower-confidence bets explicit instead of hiding uncertainty.
