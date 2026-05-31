---
name: observation-to-hypothesis-translator
render_family: tree
description: Translate observations, questions, or weak signals into alternative testable hypotheses with explicit desired outcomes, measurable signals, pass/fail logic, and data-driven decisions. Use when you need a hypothesis tree or experiment map rather than a loose brainstorming list.
---

# Observation To Hypothesis Translator

Turn observations into alternative testable hypotheses as a canonical tree artifact rooted in evidence.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- One observation, tension, or evidence-backed question.
## Structure The Tree

Turn vague assumptions into explicit experimental branches.

At minimum capture:

- one observation node
- competing hypotheses, not just one preferred answer
- at least one experiment under each viable hypothesis
- desired outcome for each experiment
- measurable signal and pass/fail rule
- explicit decision to take if the experiment passes or fails
- assumptions, risks, and unanswered questions

Preserve uncertainty honestly. If an observation supports multiple plausible explanations, keep those branches distinct rather than collapsing them prematurely.

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
2. A single-file HTML page rendering the artifact as an interactive tree (collapsible parent-child hierarchy with branching). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

