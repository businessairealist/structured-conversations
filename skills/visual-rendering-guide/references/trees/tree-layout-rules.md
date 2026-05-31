# Tree Layout Rules

## Purpose
This file defines phase-1 layout rules for tree artifacts.

Its goal is to keep hierarchical visuals readable, stable across rerenders, and
safe for reuse by tree-producing skills.

These rules apply to artifacts such as impact maps, opportunity-solution trees,
and hypothesis trees.

## Scope
This file governs arrangement and rendering expectations for hierarchical
artifacts that use parent-child structure as the primary organizing model.

It focuses on branch structure, node grouping, reading direction, spacing,
connector behavior, and rerender stability. It does not replace the shared
contracts for schema, lifecycle, artifact location, or update integrity.

## Tree Artifact Expectations
Tree artifacts normally produce the following package:

- the structured markdown output
- the human-readable summary

HTML is expected. Mermaid is commonly appropriate for tree artifacts when the
hierarchy can be represented faithfully.

## Core Layout Principles
- The hierarchy must be visually obvious without requiring explanation.
- Parent-child relationships should be clearer than decorative styling.
- The dominant reading path should stay consistent across rerenders.
- Unchanged branches should remain stable during partial updates.
- A node should have one clear parent unless canonical content explicitly models another pattern.
- Visual layout should support inspection of branching, not obscure it.

## Preferred Tree Structure
Tree layouts should emphasize:

- root or outcome node
- branch levels
- parent-child connectors
- optional sibling grouping
- stable node ordering within each branch

Use the smallest layout structure that preserves hierarchical meaning. Do not
force board, matrix, or free-canvas behavior onto a tree artifact.

## Reading Direction Rules
Unless the artifact family clearly requires another orientation, tree layouts
should use one consistent primary direction:

- left to right for outcome-to-branch structures
- top to bottom when vertical hierarchy is easier to review

Rules:

- the primary direction must be consistent across the tree
- sibling order should be deterministic
- level spacing should be regular enough that depth is easy to detect
- branch crossings should be minimized

## Root, Levels, and Branches
The root should be visually dominant and easy to identify.

Rules:

- level boundaries should be visually legible
- nodes at the same depth should align clearly where practical
- branch labels should come from canonical content, not renderer invention
- deep branches should remain traceable back to their ancestors without guesswork

Typical examples:

- impact map: goal to actors to impacts to deliverables
- opportunity-solution tree: outcome to opportunities to solutions to experiments
- hypothesis tree: observation or problem to hypotheses to tests or decisions

## Node Placement
Nodes should be placed to support rapid branch tracing.

Rules:

- sibling nodes should cluster near their parent
- large gaps should not imply false semantic separation
- unrelated branches should not visually merge
- preserve node anchors where practical during bounded updates
- avoid diagonal scatter or ornamental placement

## Connectors
Connectors are normally required for tree artifacts because they carry the
hierarchical reading path.

Rules:

- connectors should clearly indicate parent-child direction
- connector styling should not overpower node labels
- connector crossings should be minimized
- if a branch relationship is ambiguous in the visual, the layout is not acceptable

## Grouping
Grouping may be used to emphasize levels, sibling sets, or branch families.

Rules:

- grouping should reinforce the hierarchy, not replace it
- groups should not suggest additional semantics not present in canonical content
- branch clusters should stay visually separate when they represent distinct strategic paths

## HTML and Mermaid Guidance
HTML is the default review surface for tree artifacts.

Mermaid is usually appropriate for tree artifacts and should normally be
generated when the hierarchy is clear and not excessively dense.

Mermaid should be omitted when:

- annotations are too dense to preserve faithfully
- a branch uses layout richness Mermaid cannot represent well
- interaction or layered detail is necessary for accurate review

## Layout Metadata Expectations
consistently.

Typical fields may include:

- orientation
- level definitions
- node ordering
- branch grouping
- anchor positions
- spacing hints

If depth or grouping carries semantic meaning, that meaning must also be
represented canonically in the structured markdown output.

## Rerender and Update Stability
Tree rerenders should preserve the following whenever artifact identity stays the same:

- stable node identifiers
- unchanged branch order where possible
- consistent root placement
- deterministic render paths
- unchanged subtree structure outside the requested update

Partial updates must not silently reorder siblings, move unrelated branches, or
rewrite connector semantics for untouched parts of the tree.

## Failure and Clarification Rules
Stop and ask for clarification when any of the following is true:

- the artifact is not truly hierarchical
- one node appears to need multiple parents but the meaning is unclear
- the requested change would restructure large parts of the tree
- Mermaid would materially lose branch meaning
- different branch orders would imply different interpretations

## Phase-1 Intent
Phase 1 should favor clarity over density.

The priority order is:

1. clear hierarchy
2. stable branch structure
3. deterministic rerendering
4. readable HTML
5. Mermaid when it remains faithful

## Visual Design Integration

Tree artifacts use the **Mermaid / Flow** visual family from `design-system.md`.

### Mermaid rendering
Trees are the primary Mermaid output family. Apply the teal/cyan palette via `mermaid.initialize()` with custom `themeVariables` as specified in `visual-rendering-mermaid.md`.

### Interaction controls
Every Mermaid tree must include zoom in/out/reset buttons, Ctrl/Cmd+scroll zoom, and click-drag panning. See `visual-rendering-mermaid.md` for the complete implementation.

### Node styling by level
Use Mermaid node classes or inline styling to differentiate tree levels:

| Level | Style intent | Example |
|---|---|---|
| Root (goal/outcome) | Primary color, bold border | `primaryColor` + `primaryBorderColor` |
| Level 1 (actors/opportunities) | Secondary color | `secondaryColor` + `secondaryBorderColor` |
| Level 2 (impacts/solutions) | Default surface | Default node styling |
| Level 3 (deliverables/experiments) | Tertiary/muted | `tertiaryColor` + `tertiaryBorderColor` |

### HTML fallback
When Mermaid is omitted (dense annotations, complex interactions), render the tree as nested HTML using the teal/cyan CSS tokens with indented cards showing parent-child relationships.

### Accessibility
Include a text-alternative table for every Mermaid tree diagram, listing each node with its level and parent. See `accessibility.md` for implementation patterns.
