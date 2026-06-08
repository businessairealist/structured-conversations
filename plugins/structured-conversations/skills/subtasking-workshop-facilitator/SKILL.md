---
name: subtasking-workshop-facilitator
render_family: plan
description: Facilitate a subtasking session from code review through sequence thinking to implementation subtasks. Use when you need to create a workshop-ready artifact with prompts, facilitation flow, and captured implementation work.
---

# Subtasking Workshop Facilitator

Facilitate the subtasking workflow from current code review through interaction flow to actionable implementation subtasks.


Use `subtasking-template-generator` when you only need the reusable board shell. Use this skill when you need prompts, agenda flow, and project-specific facilitation framing.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- workshop topic, story, or implementation context

Optional inputs:

- code-review findings
- sequence notes
- explicit team constraints or desired workshop length
## Facilitate The Workflow

Structure the session in this order:

1. current code review
2. code modification discussion and ideas
3. sequence diagram or interaction flow
4. implementation subtasks

At each stage:

- restate the purpose of the section
- ask the smallest useful prompts
- capture decisions, risks, and open questions
- keep traceability between earlier discussion and final subtasks

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the result:

- mirrors the full subtasking workflow,
- helps the team move from discussion to implementable work,
- keeps earlier risks visible in the final tasks,
- and does not collapse the session into a flat task dump.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
