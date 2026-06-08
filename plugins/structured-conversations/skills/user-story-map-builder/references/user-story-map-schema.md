# User Story Map Schema


## Root Fields

- artifact identifier
- artifact type: `user-story-map`
- artifact version
- `collection`
- `created_by_skill`
- `created_at`
- `updated_at`
- `status`
- `source_artifacts`
- `inputs`
- `assumptions`
- `open_questions`
- `traceability`
- `render_targets`
- `compatible_with`
- `partial_update_supported`

## Content Shape

Store the semantic payload under `content`:

- `board_style`: `classic-user-story-map`
- `persona`
- `guide`
- `story_map`
- `classic_user_story_map`
- `sections`
- optional `context_summary`

## Story Map Shape

Store the canonical story map under `content.story_map`:

- `persona`
- `goal`
- `backbone`
- `activities`
- `release_slices`

Each `backbone[]` item should contain:

- `id`
- `label`

Each `activities[]` item should contain:

- `id`
- `label`
- `owner`
- `activity`
- `stories`

Each story should contain:

- stable `id`
- `title`
- `text`
- optional `tags`

Each `release_slices[]` item should contain:

- `id`
- `label`
- `story_refs`

## Classic Visual Contract

Store the poster/table contract under `content.classic_user_story_map`:

- `map_header`
- `map_title`
- `user_label`
- `goal_label`
- `goal_value`
- `columns`
- `releases`

Each `columns[]` item should contain:

- `id`
- `actor`
- `activity`
- `tasks`
- `stories`

Each `releases[]` item should contain:

- `id`
- `label`
- `placements`

## Renderer-Facing Sections

Store activity columns for the board renderer under `content.sections`.

Each section should contain:

- stable `id`
- activity `label`
- optional `description`
- `cards`

Each card should contain:

- stable `id`
- renderer-facing `title`
- renderer-facing `text`
- optional `tags`
