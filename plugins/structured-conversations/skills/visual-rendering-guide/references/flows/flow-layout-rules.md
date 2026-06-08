# Flow Layout Rules

## Purpose
This file defines phase-1 layout rules for flow artifacts.

Its goal is to make directional, stepwise, and process-oriented visuals easy to
follow, stable across rerenders, and safe for reuse by flow-producing skills.

These rules apply to ordered sequences, process flows, delivery flows,
dependency-oriented flows, and similar directional artifacts.

## Scope
This file governs arrangement and review expectations for visuals where the
primary meaning depends on order, transition, sequence, or directed movement.

It focuses on step order, directional connectors, branching behavior, lane use,
and rerender stability. It does not replace the shared contracts for schema,
lifecycle, artifact location, or update integrity.

## Flow Artifact Expectations
Flow artifacts generally use the standard visual render package when the flow is
truly visual:

- the structured markdown output
- the human-readable summary

HTML is expected for visual flows. Mermaid is often appropriate when the flow
can be represented faithfully as a directed diagram.

## Core Layout Principles
- The next step should be obvious at every point in the flow.
- Direction should be visually dominant.
- Branches, joins, and loops should be easy to distinguish.
- Unchanged steps should stay stable during rerenders and partial updates.
- Decorative placement must not obscure the process path.
- Reviewers should be able to trace the flow without guessing.

## Preferred Flow Structure
Flow layouts should emphasize:

- a clear start condition
- step or state nodes
- directional connectors
- explicit branches and joins
- optional lanes when ownership or stage matters

Use the smallest directional structure that preserves meaning. Do not spread a
simple flow across free-canvas placement when a stable sequence layout would be clearer.

## Direction Rules
Unless the artifact family clearly requires another orientation, flows should
default to one dominant direction:

- left to right for most process or delivery flows
- top to bottom when a vertical sequence is easier to review

Rules:

- the dominant direction should remain consistent
- backward arrows or loops should be visually distinct
- branch divergence and branch rejoin points should be easy to identify
- step order should be deterministic

## Lanes and Ownership
Lanes are optional for flow artifacts and should be used only when they add
clear review value.

Good uses include:

- role ownership
- system boundaries
- stage boundaries
- handoff visibility

Rules:

- lane labels should come from canonical content
- lanes should not create false hierarchy
- steps should not ambiguously straddle multiple lanes unless canonical content says so

## Step and Connector Rules
Flow steps should be placed to support quick path tracing.

Rules:

- related steps should be near their connector path
- connectors should show direction clearly
- crossings should be minimized
- loops should be explicit and readable
- connector styling should support meaning without overwhelming labels

## Branching Rules
Branches should only appear when there is real divergence in canonical content.

Rules:

- branch conditions should be explicit where needed
- alternative paths should remain visually separable
- joins should not imply equivalence if the paths remain semantically distinct
- the renderer must not invent missing branch logic

## HTML and Mermaid Guidance
HTML is the default review surface for visual flows.

Mermaid is often appropriate for flows and should normally be generated when
the flow can be represented faithfully as a directed diagram.

Mermaid should be omitted when:

- the flow depends on dense annotations or layered metadata
- lane richness is important and Mermaid would flatten meaning
- the visual depends on layout features Mermaid cannot express reliably

## Layout Metadata Expectations

Typical fields may include:

- orientation
- step ordering
- lane definitions
- branch and join hints
- anchor positions
- spacing rules

If ownership, state type, or branch meaning is semantically important, that
meaning must also exist in canonical content.

## Rerender and Update Stability
Flow rerenders should preserve the following whenever artifact identity stays the same:

- stable step identifiers
- unchanged step order where untouched
- stable branch structure outside the requested change
- deterministic derivative paths
- consistent orientation unless explicitly changed

Partial updates must not silently reroute unrelated steps, reverse connector
direction, or collapse distinct branches into a simpler flow.

## Failure and Clarification Rules
Stop and ask for clarification when any of the following is true:

- the artifact is better modeled as a board, tree, or matrix
- branch logic is ambiguous
- the requested change would materially restructure the whole flow
- Mermaid would lose important lane or annotation meaning
- multiple path interpretations would change the canonical meaning

## Phase-1 Intent
Phase 1 should prefer highly legible process structure over ambitious layout.

The priority order is:

1. clear direction
2. branch clarity
3. stable step ordering
4. readable HTML
5. Mermaid when the flow remains faithful
