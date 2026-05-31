---
name: defect-report-writer
render_family: form
description: Write or update a reproducible defect report from observations, notes, screenshots, logs, and prior triage artifacts. Use when you need a severity-aware bug report with impact, environment, reproduction steps, expected behavior, actual behavior, and supporting context.
---

# Defect Report Writer

Write a triage-ready defect report as a canonical form artifact rooted in evidence.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- A defect observation, failure note, or prior defect context.
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Try to locate the strongest existing defect observation, screenshots, logs, and prior defect artifacts before asking the user to paste them again.
- If one defect context clearly matches, use it and tell the user what was selected.
- If multiple plausible defect artifacts exist, present a short choice list based on title, status, and recency.
- Default the user review surface to the readable report, not raw canonical JSON.
- After generation, tell the user to review impact, reproduction steps, and expected versus actual behavior.

## Structure The Report

Make the report immediately usable by QA, engineering, and product.

At minimum capture:

- one clear title that names the failing behavior
- impact statement and affected actor or workflow
- reproducibility confidence
- explicit prerequisites or test data
- ordered reproduction steps
- expected versus actual outcome
- evidence links and traceability to source notes or artifacts
- assumptions and open questions that still block certainty

Prefer evidence-backed wording over speculation. If the failure is not yet reproducible, state that plainly and preserve the strongest known clues.

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

