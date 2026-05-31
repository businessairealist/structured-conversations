---
name: defect-reproduction-scaffolder
render_family: form
description: Scaffold or update a reproducible defect path from observations, screenshots, logs, support notes, and prior defect artifacts. Use when you need a disciplined reproduction flow with setup, exact steps, expected results, actual results, and blockers to reproducibility.
---

# Defect Reproduction Scaffolder

Turn a failure observation into a reproducible defect path as a canonical quality artifact.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- A defect observation or symptom description.
## Structure The Reproduction Path

Make the scaffold executable by someone who did not witness the original failure.

At minimum capture:

- starting environment and prerequisites
- data or account setup
- ordered steps with exact actions where known
- expected result for each critical checkpoint
- actual failing result
- reproducibility rating such as always, intermittent, or not yet confirmed
- suspected variables that may affect reproduction
- blockers, unknowns, and next diagnostic steps

If evidence is weak, separate confirmed facts from hypotheses. Do not quietly convert guesses into deterministic steps.

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

