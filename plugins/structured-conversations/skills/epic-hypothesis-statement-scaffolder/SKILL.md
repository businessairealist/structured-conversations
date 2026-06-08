---
name: epic-hypothesis-statement-scaffolder
render_family: form
description: Scaffold a decision-ready epic hypothesis statement from standard fields. Use when you need a structured first draft before a polished epic statement is fully authored.
---

# Epic Hypothesis Statement Scaffolder

Scaffold a structured epic hypothesis statement artifact from the standard epic fields.


Use this skill when the team has partial epic inputs and needs a coherent first draft before refining it with `outcome-driven-epic-writer`.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- an epic name or epic context

Optional inputs:

- funnel entry date
- owner
- description
- business outcomes
- product OKR
- leading indicators
- nonfunctional requirements
## Scaffold The Statement

Use this sequence:

1. Preserve the standard epic-hypothesis fields.
2. Fill known fields with concrete draft content.
3. Turn missing fields into clear fill-in prompts rather than leaving gaps.
4. Produce a readable first-pass statement that can be refined later.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the scaffold:

- preserves every standard epic field,
- distinguishes drafted content from missing-field prompts,
- remains readable as a first-pass statement,
- and stays easy to refine into a completed epic artifact.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
