---
name: mapping-technique-selector
render_family: tree
description: Diagnose an alignment problem and recommend which mapping technique to use, with a lightweight facilitation plan and expected outputs. Use when you need to choose between discovery and planning map formats such as empathy maps, impact maps, journey maps, value stream maps, story maps, opportunity-solution trees, feature maps, or example maps based on the team’s problem, evidence, and desired outcome.
---

# Mapping Technique Selector

Use this skill to choose the best mapping technique for an alignment, discovery, planning, or clarification problem and to provide a lightweight facilitation path into the right downstream mapping skill.


Use `verb-noun-rewriter` first when the source language is still too vague, and use `syntax-pattern-selector` first when the main blocker is statement framing rather than mapping structure.

Read [mapping-technique-selector.md](././references/foundation/mapping-technique-selector.md) for the selection workflow, routing heuristics, and output template.

Read [map-technique-decision-tree.md](././references/foundation/map-technique-decision-tree.md) for the technique catalog and quick routing guide.

Read these shared references when project-runtime details matter:

- [workspace-contract.md](././references/shared/workspace-contract.md)
- [artifact-location-rules.md](././references/shared/artifact-location-rules.md)
- [artifact-naming-conventions.md](././references/shared/artifact-naming-conventions.md)
- [artifact-schema.md](././references/shared/artifact-schema.md)

## Find Inputs

Treat these as required inputs:

- Context of the alignment problem, planning problem, or discovery problem.
- Desired outcome for the conversation or artifact.

Treat these as optional inputs:

- Available evidence or source material.
- Workshop participants, meeting length, or facilitation style.
- Preferred downstream artifact family or constraints on visual complexity.

Resolve inputs in this order:

1. Explicit artifact or path arguments from the user request.
3. `intake/`
4. `inputs/notes/`
5. `artifacts/shared/`
6. `artifacts/foundation/`

If no valid input can be found, ask for the missing artifact name or location. Ask for the smallest missing piece only.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Treat this skill as a front door: the user should be able to start from a problem statement rather than a known technique.
- Try to locate current notes and prior artifacts first before asking the user for more context.
- Present technique recommendations in plain language with why each option fits.
- Make one recommended next step explicit.

## Run the Selection Workflow

Use this sequence:

1. Identify the core alignment problem.
2. Determine whether the main need is empathy, journey understanding, outcome mapping, process flow, solution branching, feature clarification, example clarification, or release planning.
3. Compare the relevant map families against the context and available evidence.
4. Select the best-fit mapping technique and explain why it fits better than the alternatives.
5. Draft a lightweight facilitation plan with opening prompt, core questions, and expected output.
6. Recommend the downstream mapping skill that should build or facilitate the chosen artifact.
7. Preserve traceability between the source problem and the recommendation.

Prefer the smallest map that makes the team’s decision clearer.

Stop and ask for clarification instead of guessing when:

- the request could reasonably map to multiple very different artifact families,
- the desired outcome is unclear,
- the available evidence materially changes the map choice,
- or the upstream artifact referenced in the request cannot be resolved safely.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact as an interactive tree (collapsible parent-child hierarchy with branching). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

Ensure the output:

- chooses the map based on the problem structure, not familiarity,
- gives a practical next step into a downstream mapping skill,
- uses a facilitation plan that is lightweight but actionable,
- surfaces meaningful tradeoffs between techniques when relevant,
- and reduces ambiguity instead of simply listing map options.

If the source already clearly points to one mapping technique, say so and produce a minimal artifact that records the recommendation and next step.
