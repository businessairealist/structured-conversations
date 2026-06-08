---
name: subtasking-template-generator
render_family: plan
description: Generate a reusable subtasking board template. Use when you need a workshop-ready board with code-review, implementation-ideas, sequence-diagram, and subtask sections before real project-specific content is added.
---

# Subtasking Template Generator

Generate a reusable subtasking board that teams can fill in during planning or workshop sessions.


Use this skill when the goal is to create a repeatable board structure, not to fully decompose a specific story. Use `subtasking-workshop-facilitator` when the session should already contain prompts and live facilitation guidance.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- optional title or workshop context for the board

Optional inputs:

- whether the template should include example prompts
- a preferred section order or emphasis
## Generate The Template

Create a board with these default sections:

1. current code review
2. code modification discussion and ideas
3. sequence diagram or interaction flow
4. implementation subtasks

Use clear prompts that help a team capture:

- current behavior and extension points
- likely implementation changes
- interaction sequence or dependency flow
- actionable subtasks, handoffs, and open questions

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the template:

- is reusable across teams and stories,
- gives each board section a clear purpose,
- and matches the same subtasking flow used by the workshop and planner skills.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
