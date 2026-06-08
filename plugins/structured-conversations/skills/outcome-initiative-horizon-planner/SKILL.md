---
name: outcome-initiative-horizon-planner
render_family: matrix
description: Place candidate initiatives into Now, Next, or Later based on confidence, evidence, dependencies, urgency, and outcome linkage. Use when you need a defensible horizon recommendation before building a roadmap board.
---

# Outcome Initiative Horizon Planner

Plan horizon placement for candidate initiatives before they are rendered into a roadmap artifact.


Use this skill when the team has multiple candidate bets and needs a clear recommendation for which work belongs in `Now`, `Next`, or `Later`. This skill is especially useful before `goal-oriented-roadmap-builder` or `now-next-later-roadmap-scaffolder`.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one strategic goal
- one or more candidate initiatives

Optional inputs:

- target outcomes
- customer needs
- evidence or confidence signals
- dependencies or sequencing constraints
- urgency notes
## Plan Horizons

Use this sequence:

1. Confirm the goal and what outcomes matter most.
2. List candidate initiatives, including evidence, dependencies, and outcome linkage where available.
3. Recommend `Now`, `Next`, or `Later` based on confidence, readiness, and sequencing.
4. Capture rationale and open questions rather than forcing weak bets into `Now`.

Prefer a transparent recommendation over fake precision. Horizon placement should be easy to explain to a product, design, or engineering team.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Generate Mermaid when the horizon recommendation can be represented faithfully.

## Quality Bar

Ensure the output:

- recommends horizons with clear rationale,
- keeps outcomes visible,
- shows which bets are blocked by dependencies or weak evidence,
- and leaves uncertainty explicit instead of hiding it.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
