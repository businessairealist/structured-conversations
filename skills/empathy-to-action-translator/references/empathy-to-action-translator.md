# Empathy To Action Translator Reference

Use this skill to turn a completed empathy map into a reusable downstream action artifact.

The current translator produces a canonical board artifact of type `empathy-action-translation` that preserves the upstream actor and converts empathy-map signals into action-oriented sections for follow-on planning.

## Primary Script

Use this script entrypoint for the empathy translation workflow:


## Required Upstream Artifact

Required:

- A completed `empathy-map` artifact already saved under `artifacts/`, or equivalent structured empathy evidence that can be resolved into one.

Optional:

- Preferred downstream direction such as goals, impact map input, journey hypotheses, story seeds, or roadmap framing.
- Specific empathy-map artifact ID or slug.

## Search Order

Look for usable inputs in this order:

1. Explicit paths or artifact names from the request.
2. Project manifest aliases and prior run metadata.
3. `intake/`
4. `inputs/source_docs/`
5. `inputs/source_images/`
6. `inputs/notes/`
7. `artifacts/foundation/`
8. `artifacts/mapping/`
9. `artifacts/shared/`
10. Latest compatible artifact from the workspace

Ask the user only if the upstream artifact is still missing or ambiguous after the search.

## Translation Rules

- Preserve the upstream actor context from the empathy map.
- Keep traceability back to the source empathy artifact.
- Treat generated outputs as scaffolding, not final delivery commitments.
- Mark inferred action recommendations clearly.
- Carry forward open questions where evidence is weak or missing.

## Output Contract

Write the translated artifact to:

the working directory<artifact-slug>/`

Expected files:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions


## Canonical Content Shape

The current implementation writes these sections into the structured markdown output:

- `goals` with label `Verb + Noun Goals`
- `opportunities` with label `Opportunity Areas`
- `journey-hypotheses` with label `Journey Hypotheses`
- `story-seeds` with label `Story Seeds`

Each generated card should preserve:

- a stable card title or label,
- the source empathy evidence text,
- source references back to the empathy map,
- inference markers where applicable.

## Supporting Scripts

Check these implementation paths when you need runtime detail:


## Related Skills

- `verb-noun-rewriter`
- `syntax-pattern-selector`
- `empathy-map-builder`
- `impact-map-builder`
