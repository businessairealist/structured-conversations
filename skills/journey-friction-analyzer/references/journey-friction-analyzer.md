# Journey Friction Analyzer Reference

Use this skill to analyze a completed customer journey map and identify the stages where the customer is most likely experiencing friction.

## Primary Scripts


## Inputs

Required:

- A completed `customer-journey-map` artifact.

Optional:

- A specific artifact ID or slug.
- A prior friction-analysis artifact for comparison.

## Output Contract

Write the friction analysis to:

the working directory<artifact-slug>/`

Expected files:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

## Canonical Content Shape

The analyzer writes a board artifact with:

- `persona`
- `analysis`
- `sections`

The `analysis` block should preserve:

- `source_journey_map`
- `ranked_friction`
- `signal_summary`
- `improvement_candidates`

The renderer-facing `sections` should expose those same analysis slices as readable board columns.

## Related References

- `references/mapping/journey-friction-rubric.md`
- `references/mapping/customer-journey-map-schema.md`
