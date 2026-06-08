# Customer Journey Map Builder Reference

Use this skill to turn customer evidence into a reusable classic customer-journey poster artifact for one persona.

## Primary Scripts


## Inputs

Required:

- Persona or customer segment.
- Stage, touchpoint, or experience evidence.

Optional:

- Explicit stage list.
- Existing journey map artifact to update.

## Output Contract

Write the journey map to:

the working directory<artifact-slug>/`

Expected files:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

## Canonical Content Shape

The builder writes a classic customer journey layout with:

- a left guide panel
- a persona title spanning the journey columns
- a stage header row
- row bands for `activities`
- `needs`
- `experience`
- `notes-ideas`

The canonical semantic data stays under `content.journey_map`, while the renderer-facing table contract lives under `content.classic_customer_journey_map`.
