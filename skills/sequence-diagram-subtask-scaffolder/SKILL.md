---
name: sequence-diagram-subtask-scaffolder
render_family: flow
description: Use a sequence diagram or interaction flow to scaffold technical subtasks. Use when you need to convert participant interactions, request/response steps, validation checkpoints, and side effects into implementation-ready subtasks with dependency hints and testing follow-up.
---

# Sequence Diagram Subtask Scaffolder

Turn an interaction flow into concrete technical subtasks without losing the sequencing logic.


Use this skill when the team already understands the main interaction flow and needs technical decomposition from that flow. Use `code-review-to-subtask-translator` when the source is review feedback rather than a step-by-step interaction.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- sequence-diagram notes, interaction flow, or equivalent step-by-step system behavior

Optional inputs:

- associated story or acceptance artifacts
- known service boundaries, integrations, or persistence concerns
- explicit sequencing constraints or ownership hints
## Scaffold The Subtasks

Use this sequence:

1. Identify the participants and the ordered interaction steps.
2. Preserve the main validation, state change, and side-effect checkpoints.
3. Group the interaction into coherent implementation slices such as frontend, service, persistence, integration, and testing.
4. Derive subtasks that implement or harden the flow in execution order.
5. Record where the sequence suggests concurrency, retry, failure handling, or regression risks.

Prefer implementation slices that map to real interaction boundaries over vague work items such as "handle sequence diagram."

When the diagram is too incomplete to scaffold safely, record the missing interaction or data detail as an open question.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact as a process flow (directional steps, swim lanes, or sequence). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

Capture:

- source interaction flow
- participants
- ordered sequence steps
- resulting subtasks
- dependency hints
- validation or failure-path follow-up
- assumptions and open questions
- traceability from sequence steps to subtasks

## Quality Bar

Ensure the result:

- preserves the important interaction ordering,
- produces technical subtasks that can be implemented independently,
- makes state changes and side effects explicit,
- and gives `story-subtask-planner` or workshop flows a clean technical backbone.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
