# Customer Journey Map Schema


## Root Fields

- artifact identifier
- artifact type: `customer-journey-map`
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

Store the semantic and renderer-facing payload under `content`:

- `board_style`: `classic-customer-journey-map`
- `persona`
- `guide`
- `journey_map`
- `classic_customer_journey_map`
- `sections`
- optional `context_summary`

## Canonical Journey Data

Store the canonical journey data under `content.journey_map`:

- `persona`
- `stages`
- `row_order`

Each stage contains:

- `id`
- `label`
- `rows`

Each row contains:

- `id`
- `label`
- `cards`

Required row IDs:

- `activities`
- `needs`
- `experience`
- `notes-ideas`

## Classic Visual Contract

Store the poster/table render contract under `content.classic_customer_journey_map`:

- `persona_title`
- `actor_label`
- `stage_label`
- `row_labels`
- `stages`

Each `classic_customer_journey_map.stages[]` entry should contain:

- `id`
- `label`
- `tone_index`
- `activities`
- `needs`
- `experience`
- `notes_ideas`

This contract should render as:

- a left guide panel
- an actor header row
- a stage header row
- row bands for `Activities`, `Needs`, `Experience`, and `Notes, Ideas`
- one stage column per journey stage

## Renderer-Facing Sections

Keep `content.sections` as stage-based sections for generic compatibility and downstream tools.

Each section should contain:

- stable `id`
- stage `label`
- optional `description`
- `cards`
