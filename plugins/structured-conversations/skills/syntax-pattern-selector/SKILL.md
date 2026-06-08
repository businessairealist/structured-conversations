---
name: syntax-pattern-selector
render_family: matrix
description: Choose the best syntax template for a product conversation and draft the requirement, hypothesis, job story, feature definition, event rule, or constraint story in that format. Use when you need to select the right framing pattern for a requirement or problem, compare multiple syntax options, or translate fuzzy request context into a clearer statement for a specific audience or delivery context.
---

# Syntax Pattern Selector

Use this skill to choose the best framing pattern for a product, delivery, or discovery conversation and to draft the statement in that pattern.


Use `verb-noun-rewriter` first when the source wording is still too vague or overloaded to evaluate patterns fairly.

Read [syntax-pattern-selector.md](././references/foundation/syntax-pattern-selector.md) for the selection workflow, routing heuristics, and output template.

Read [syntax-patterns.md](././references/foundation/syntax-patterns.md) for the pattern catalog and guidance on when each syntax format fits.

Read these shared references when project-runtime details matter:

- [workspace-contract.md](././references/shared/workspace-contract.md)
- [artifact-location-rules.md](././references/shared/artifact-location-rules.md)
- [artifact-naming-conventions.md](././references/shared/artifact-naming-conventions.md)
- [artifact-schema.md](././references/shared/artifact-schema.md)

## Find Inputs

Treat these as required inputs:

- Context of the requirement or problem.
- Desired audience or delivery context.

Treat these as optional inputs:

- Risk level.
- Experimentation intent.
- System-versus-user orientation.

Resolve inputs in this order:

1. Explicit artifact or path arguments from the user request.
3. `intake/`
4. `inputs/notes/`
5. `artifacts/shared/`
6. `artifacts/foundation/`

If no valid input can be found, ask for the missing artifact name or location. Ask for the smallest missing piece only.

## Run the Selection Workflow

Use this sequence:

1. Identify the source problem, request, or requirement statement.
2. Determine the audience, delivery need, and decision context.
3. Compare the relevant syntax patterns against the context.
4. Select the best-fit pattern and explain why it fits better than the alternatives.
5. Draft the statement in the selected pattern.
6. Record rejected alternatives when they clarify tradeoffs or future options.
7. Preserve traceability between the source wording and the drafted statement.

Prefer the lightest syntax that creates clarity without overfitting the request.

Stop and ask for clarification instead of guessing when:

- the source context is too vague to distinguish between competing patterns,
- the audience or delivery context materially changes the recommendation,
- multiple patterns are equally plausible and would lead to different downstream artifacts,
- or the upstream artifact referenced in the request cannot be resolved safely.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the output:

- chooses a pattern based on purpose, not preference,
- produces a draft statement that another skill or teammate can use immediately,
- surfaces meaningful tradeoffs between formats when relevant,
- avoids unnecessary template ceremony,
- and leaves downstream work with less ambiguity than the source context had.

If the source is already in the right pattern, say so and produce a minimal artifact that records the pattern as already suitable.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
