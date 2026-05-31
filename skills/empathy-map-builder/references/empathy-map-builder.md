# Empathy Map Builder Reference

Use this skill to turn customer evidence into a reusable empathy-map board artifact for one actor.

The finalized empathy-map artifact should render in the classic empathy-mapping poster layout: a left guidance panel, top `who` and `goal` areas, side wedges for `hear`, `see`, and `say`, a bottom `do` lane, and a central think/feel area split into pains and gains.

## Primary Scripts

Use these script entrypoints for the empathy-map workflow:


## Inputs

Required:

- Actor or persona name.
- Evidence such as interview notes, quotes, tickets, support logs, screenshots, or observations.

Optional:

- Segment tags.
- Confidence levels.
- Existing empathy-map artifact to update.

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

## Synthesis Rules

- Build the map for a single actor unless the user explicitly asks for comparison.
- Prefer evidence-backed cards over generic persona language.
- Keep direct quotes separate from interpretation.
- Mark inferred thoughts and feelings as inference.
- Capture ambiguity in open questions.

## Output Contract

Write the empathy map to:

the working directory<artifact-slug>/`

Expected files:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions


The HTML and SVG renders should favor the classic empathy-map poster composition rather than a generic column board whenever the artifact type is `empathy-map`, `empathy-map-template`, or `empathy-map-workshop`.

## Update Rules

- Update the structured markdown output first.
- Preserve unchanged cards and stable IDs.
- Regenerate render outputs only after the structured markdown output is valid.
- Record the requested patch and preserved sections in execution notes.

For implementation details, check:

