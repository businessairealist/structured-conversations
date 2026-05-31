# Empathy Map Schema


The canonical `content` payload should carry enough metadata for the renderer to produce the classic empathy-map poster layout shown in the reference example.

Model the empathy map as a board artifact with these semantic sections in the structured markdown output:

## Root Fields

- artifact identifier
- artifact type: `empathy-map`
- artifact version
- `collection`: `mapping-discovery`
- `created_by_skill`: `empathy-map-builder`
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

- `actor`
- `sections`
- optional `context_summary`
- optional `guide`
- optional `classic_empathy_map`

Recommended section keys:

- `see`
- `hear`
- `say`
- `do`
- `think`
- `feel`

Each section should contain cards with:

- stable `id`
- renderer-facing `title`
- renderer-facing `text`
- optional `tags`

The builder currently stores actor metadata under `content.actor` and board sections under `content.sections`, where each section contains renderer-ready cards. Evidence lineage, assumptions, and open questions remain at the structured markdown output root.

When present:

- `content.guide` drives the left instructional panel.
- `content.classic_empathy_map.who` drives the top-left actor block.
- `content.classic_empathy_map.goal` drives the top-center goal block.

## Layout Shape


- board title
- section order
- lane or column coordinates
- card positions
- styling hints needed by the renderer

Keep layout detachable so the artifact can be re-rendered without rewriting the structured markdown output.

Related scripts:

