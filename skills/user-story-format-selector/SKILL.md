---
name: user-story-format-selector
render_family: matrix
description: Choose the best user story format for a work item and draft the first pass in that syntax. Use when you need to select among Traditional, Hypothesis Driven Development (HDD), Feature Driven Development (FDD), Job Story, and JTBD framing, compare alternatives, or prepare a story artifact that downstream drafting, INVEST, example mapping, or subtasking work can reuse.
---

# User Story Format Selector

Choose the story format that best matches the request, then draft the story in that syntax.


Use `verb-noun-rewriter` first when the work item is still a vague noun pile. Reuse `syntax-pattern-selector` when the request may not belong in a user-story format at all.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred
## Select The Format

Evaluate these formats deliberately:

- Traditional when the actor, goal, and benefit are already clear.
- HDD when the work is really a capability plus expected measurable signal.
- FDD when the team needs action-plus-result framing around a feature.
- Job Story when situation and motivation drive the behavior.
- JTBD when the story should anchor on context, target customer, and desired outcome rather than interface language.

Use this sequence:

1. Identify the source request and its delivery context.
2. Determine whether the request is primarily user-goal, job-context, hypothesis, or feature framing.
3. Compare at least the two most plausible formats.
4. Select the best-fit syntax and explain why it fits better than the alternatives.
5. Draft the story in the chosen syntax.
6. Preserve traceability from the source wording to the drafted statement.

Prefer the lightest format that adds clarity without forcing ceremony.

Stop and ask for clarification instead of guessing when:

- the actor, job context, or intended outcome is materially ambiguous,
- multiple formats are equally plausible and would change downstream work,
- or the referenced upstream artifact cannot be resolved safely.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Include these content areas:

- source work item
- evaluated formats
- chosen format
- drafted story
- rejection notes or tradeoffs when helpful
- assumptions
- open questions
- traceability to upstream artifacts


## Quality Bar

Ensure the result:

- chooses a format because it improves the conversation, not because it is fashionable,
- produces a draft another skill can refine immediately,
- keeps alternatives visible when the tradeoff matters,
- and reduces ambiguity for `user-story-drafter`, `invest-readiness-checker`, and `example-map-builder`.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
