---
name: hypothesis-tree-template-generator
render_family: tree
description: Generate a reusable hypothesis-tree template. Use when you need a canonical scaffold for observations, hypotheses, experiments, signals, and decisions before a specific tree is fully populated.
---

# Hypothesis Tree Template Generator

Create a reusable template artifact for hypothesis-driven strategy work.


Use this skill when a team wants to run structured hypothesis thinking repeatedly and needs a consistent scaffold before specific branches are filled in.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- one title or context for the template

Optional inputs:

- observation prompt
- branch labels
- experiment prompts
- decision prompts
- evidence or signal prompts
## Generate The Template

Use this sequence:

1. Define the observation or problem framing area.
2. Provide reusable hypothesis branch prompts.
3. Include experiment, signal, and decision prompts under each branch.
4. Leave enough structure for teams to populate the template without rewriting it.

Prefer prompts that encourage alternative explanations rather than a single favored hypothesis.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact as an interactive tree (collapsible parent-child hierarchy with branching). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

Ensure the template:

- encourages multiple competing hypotheses,
- includes experiment and decision prompts,
- keeps evidence and signal thinking visible,
- and is reusable across different strategy problems.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
