# Impact Map Schema


The canonical `content` payload should carry enough metadata for the renderer to produce the classic impact-mapping poster layout shown in the reference example: a left instructional panel and five mapping columns labeled `WHY`, `WHO`, `HOW`, `WHAT`, and `VIA`.

## Root Fields

- artifact identifier
- artifact type: `impact-map`
- artifact version
- `collection`: `mapping-discovery`
- `created_by_skill`: `impact-map-builder`
- `created_at`
- `updated_at`
- `status`
- `source_artifacts`
- `inputs`
- `assumptions`
- `open_questions`
- `traceability`
- `render_targets`
- `supersedes_artifact identifier`
- `compatible_with`
- `stale_reason`
- `recompute_required_for`
- `partial_update_supported`

## Content Shape

Store the semantic payload under `content`:

- `board_style`: `classic-impact-map`
- `goal`
- `impact_map`
- `sections`
- optional `context_summary`
- optional `guide`
- optional `classic_impact_map`

## Goal Shape

Store the primary business outcome under `content.goal`:

- `statement`
- optional `metrics`
- optional `constraints`

## Branch Shape

Store the branch logic under `content.impact_map`:

- `goal`
- `branches`
- `highest_leverage_branches`

Each branch should contain:

- `actor`
- `impacts`
- `deliverables`
- `via`

This keeps the branch semantics separate from the renderer-facing section cards.

## Renderer-Facing Sections

Store renderer-friendly board sections under `content.sections` with these IDs:

- `why`
- `who`
- `how`
- `what`
- `via`

Each section should contain:

- stable `id`
- renderer-facing `label`
- optional `description`
- `cards`

Each card should contain:

- stable `id`
- renderer-facing `title`
- renderer-facing `text`
- optional `tags`

## Classic Impact Layout Metadata

When present, `content.guide` drives the left instructional panel:

- `title`
- optional `quote`
- `purpose`
- `audience`
- `process_steps`
- optional `legend`

When present, `content.classic_impact_map` drives the specialized impact-map poster renderer:

- `why`
- `who`
- `how`
- `what`
- `via`
- `rows`

Recommended meanings:

- `why`: organizational objective cards
- `who`: personas, users, or actors
- `how`: impacts or behavior changes
- `what`: deliverables or outcomes
- `via`: user stories or hypotheses
- `rows`: aligned actor-to-impact-to-deliverable-to-via branch records

## Layout Shape


- board title
- column order
- section order
- stable card ordering
- styling hints needed by the renderer

Keep layout detachable so the artifact can be re-rendered without rewriting the structured markdown output.

Related scripts:

