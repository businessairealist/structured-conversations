---
name: verb-noun-rewriter
render_family: form
description: Rewrite vague goals, backlog items, requirements, initiatives, and noun piles into precise verb-plus-noun statements and decompose overloaded items into smaller actionable units. Use when you need to tighten fuzzy language, split bundled work, or create clearer foundation artifacts from ambiguous request intake, notes, or prior artifacts.
---

# Verb-Noun Rewriter

Use this skill to convert vague topic statements into clearer action-oriented language that downstream skills can reuse safely.


Read [verb-noun-rewriter.md](././references/foundation/verb-noun-rewriter.md) for the rewrite workflow and output shape.

Read [verb-noun-guide.md](././references/foundation/verb-noun-guide.md) when you need heuristics for spotting noun piles, weak verbs, bundled requests, or decomposition patterns.

Read these shared references when project-runtime details matter:

- [workspace-contract.md](././references/shared/workspace-contract.md)
- [artifact-location-rules.md](././references/shared/artifact-location-rules.md)
- [artifact-naming-conventions.md](././references/shared/artifact-naming-conventions.md)
- [artifact-schema.md](././references/shared/artifact-schema.md)

## Find Inputs

Treat these as required inputs:

- A vague backlog item, requirement, initiative, problem statement, or noun pile.

Treat these as optional inputs:

- Domain verb list.
- Banned words.
- Preferred output style or level of decomposition.

Resolve inputs in this order:

1. Explicit artifact or path arguments from the user request.
3. `intake/`
4. `inputs/notes/`
5. `artifacts/shared/`
6. `artifacts/foundation/`

If no valid input can be found, ask for the missing item or artifact location. Ask for the smallest missing piece only.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Try to locate the best existing fuzzy statement, notes, or prior artifact before asking the user to paste content again.
- If one strong match exists, use it and tell the user what was selected.
- If multiple plausible inputs exist, present a short choice list based on topic and recency.
- Ask for pasted or uploaded content only when no suitable input can be located safely.
- After generating the rewrite, tell the user what to review and what a likely next step is.

## Run the Rewrite Workflow

Use this sequence:

1. Identify the original statement and any referenced upstream artifacts.
2. Detect ambiguity, noun piles, bundled requests, missing actors, or weak action words.
3. Rewrite the item into one or more precise verb-plus-noun statements.
4. Decompose the item when the original statement contains multiple intentions, multiple deliverables, or multiple decisions.
5. Preserve traceability between the original statement and each rewrite.
6. Record assumptions, banned alternatives when useful, and any open questions that block a stronger rewrite.

Prefer concrete actions over abstract aspirations. Rewrite toward language another skill can consume directly.

Stop and ask for clarification instead of guessing when:

- the source statement refers to unknown domain jargon that changes the meaning,
- multiple competing rewrites are equally plausible,
- decomposition would require inventing hidden scope,
- or an upstream artifact is referenced but cannot be resolved safely.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the output:

- replaces vague nouns with observable actions and objects,
- avoids generic verbs such as `handle`, `manage`, or `support` unless the domain truly requires them,
- splits overloaded scope into smaller coherent units,
- stays faithful to the source without inventing requirements,
- and leaves downstream skills with clearer routing and less ambiguity.

If the source item is already specific enough, say so and produce a minimal rewrite artifact that records the statement as already usable.
