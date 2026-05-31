# Release Slice Planner Reference

Use this skill to translate a completed user story map into a reusable release-slice planning artifact.

## Primary Scripts


## Inputs

Required:

- A completed `user-story-map` artifact.

Optional:

- A specific story-map artifact ID or slug.
- A maximum number of slices to include.

## Output Contract

Write the release-slice plan to:

the working directory<artifact-slug>/`

Expected files:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

## Canonical Content Shape

The planner writes a board artifact with:

- `persona`
- `planning`
- `sections`

The `planning` block should preserve:

- `source_story_map`
- `goal`
- `release_slices`
- `planned_summaries`
- `risks`

The renderer-facing `sections` should expose the slice plan and risk checks as readable board columns.
