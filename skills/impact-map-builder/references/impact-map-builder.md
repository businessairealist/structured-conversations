# Impact Map Builder Reference

Use this skill to turn a business goal, known actors, and behavior-change hypotheses into a reusable impact-map board artifact.

The finished artifact should connect an outcome to actors, impacts, and deliverables so teams can reason about leverage, gaps, and downstream delivery choices.

The finalized impact-map artifact should render in the classic impact-mapping poster layout: a left guidance panel and five aligned columns labeled `WHY`, `WHO`, `HOW`, `WHAT`, and `VIA`.

## Primary Script

Use this script entrypoint for the impact-map workflow:


This builder is expected to rely on the shared workspace helpers for scaffold creation, artifact lookup, rendering, execution records, and artifact registration.

## Inputs

Required:

- Business goal.
- Known actors.
- Behavior-change hypotheses or customer insights.

Optional:

- Existing initiatives or deliverables.
- Constraints.
- Success metrics.
- Existing impact-map artifact to update.

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

- Start from a clearly worded business outcome.
- Branch to actors whose behavior matters for that outcome.
- Branch from each actor to behavior-change impacts before proposing deliverables.
- Keep deliverables as hypotheses or candidate interventions, not predetermined commitments.
- Break deliverables into `VIA` items such as user stories or hypotheses when possible.
- Note weak links, missing evidence, and ambiguous branches in open questions.

## Output Contract

Write the impact map to:

the working directory<artifact-slug>/`

Expected files:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions


## Expected Outcomes

The skill should produce:

- an impact map,
- likely highest-leverage branches,
- a gaps or questions list.

The canonical visual model should map to:

- `WHY`: goals or objectives
- `WHO`: actors or personas
- `HOW`: impact statements
- `WHAT`: deliverables or outcomes
- `VIA`: user stories or hypotheses

## Supporting Scripts

Check these implementation paths when you need runtime detail:


## Related Skills

- `verb-noun-rewriter`
- `syntax-pattern-selector`
- `impact-map-facilitator`
- `impact-to-story-translator`
- `empathy-to-action-translator`
