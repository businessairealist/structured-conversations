# User Story Map Builder Reference

Use this skill to turn actor, workflow, and delivery evidence into a reusable classic user-story-map board artifact.

## Primary Scripts


## Inputs

Required:

- Persona or actor.
- Primary user goal.

Optional:

- Backbone activities.
- Explicit stories or task notes.
- Release slices.
- Existing story-map artifact to update.

## Output Contract

Write the story map to:

the working directory<artifact-slug>/`

Expected files:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

## Canonical Content Shape

The builder writes a story map with:

- `board_style`: `classic-user-story-map`
- `persona`
- `guide`
- `story_map`
- `classic_user_story_map`
- `sections`
- optional `context_summary`

The canonical `story_map` payload preserves:

- `goal`
- `backbone`
- `activities`
- `release_slices`

The `classic_user_story_map` payload preserves the poster-facing structure:

- summary cards for `user` and `goal`
- activity columns with actor and activity bands
- user task cards
- user story cards
- release rows

Each activity still becomes a renderer-facing board section while the semantic story-map structure remains under `content.story_map`.
