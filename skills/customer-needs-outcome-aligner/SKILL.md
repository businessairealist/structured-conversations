---
name: customer-needs-outcome-aligner
render_family: matrix
description: Align candidate initiatives against customer needs and target outcomes. Use when you need a defensible need-to-outcome trace before committing bets to a roadmap.
---

# Customer Needs Outcome Aligner

Create a reusable alignment artifact that shows which initiatives actually support customer needs and measurable outcomes.


Use this skill before roadmap planning when teams are arguing about what matters, or when a roadmap already exists but the value logic behind it is weak.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one or more customer needs
- one or more target outcomes
- one or more candidate initiatives

Optional inputs:

- evidence or confidence notes
- assumptions
- dependencies
- strategic goal or framing statement
## Build Alignment

Use this sequence:

1. Confirm the customer needs and the outcomes that matter.
2. Review each initiative for explicit linkage to those needs and outcomes.
3. Mark alignment as strong, partial, or weak.
4. Keep unsupported bets visible as assumptions or open questions instead of silently promoting them.

Use plain language. The output should help teams challenge weak bets without requiring a second translation step.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Generate Mermaid when the alignment can be represented faithfully.

## Quality Bar

Ensure the artifact:

- makes need-to-outcome linkage explicit,
- highlights weak or missing support,
- gives each initiative a usable alignment rationale,
- and stays compatible with roadmap planning work.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
