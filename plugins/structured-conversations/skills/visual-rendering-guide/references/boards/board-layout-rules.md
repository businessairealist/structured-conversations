# Board Layout Rules

## Purpose
This file defines phase-1 layout rules for board and canvas artifacts.

Its goal is to make board-like outputs readable, stable across rerenders, and
safe for reuse across multiple board-producing skills.

These rules apply to artifacts such as empathy maps, journey maps, feature
maps, example maps, user story maps, sub-tasking boards, roadmaps, and OKR
maps.

## Scope
This file governs visual layout expectations for board and canvas artifacts.

It focuses on arrangement, grouping, lanes, columns, rows, spatial hierarchy,
and stable board rendering behavior. It does not replace the shared contracts
for canonical schema, artifact location, lifecycle, or update integrity.

## Relationship to Shared Contracts
This file assumes the following shared rules already apply:

- the structured markdown output is the semantic source of truth.
- HTML is the default render target for visual artifacts.
- Mermaid is optional and must be omitted when fidelity would be poor.
- Rerenders must preserve unchanged content and avoid unrelated drift.

## Board Artifact Expectations
Board and canvas artifacts normally produce the following package:

- the structured markdown output
- the human-readable summary

Board artifacts are visual by default. They should normally render to HTML and
carry explicit layout metadata because review depends on structure and
placement.

## Core Layout Principles
- Layout must reflect canonical semantic structure instead of inventing it.
- Spatial grouping should make relationships easier to review, not hide them.
- The most important organizing dimension should be visually dominant.
- Unchanged sections should remain stable across rerenders and partial updates.
- Dense boards should still read in a predictable left-to-right and top-to-bottom order.
- Boards should be understandable without requiring pixel-perfect placement.

## Preferred Board Structure
Board layouts should use a small number of explicit structural primitives:

- lanes
- columns
- rows
- groups or clusters
- cards or nodes
- optional connectors

Skills should choose the smallest layout structure that preserves meaning.
Avoid adding decorative placement logic that is not tied to reviewable value.

## Layout Direction Rules
Unless the artifact family clearly needs another orientation, board layouts
should follow these defaults:

- primary flow: left to right
- secondary grouping: top to bottom
- card order within a section: stable and deterministic
- section order: stable across rerenders

If a board uses vertical progression as the dominant reading path, that choice

## Lanes, Columns, and Rows
Use lanes, columns, and rows only when they carry meaningful review structure.

Examples:

- empathy map: named sections around the actor and their observations
- journey map: stage columns with consistent supporting rows
- story map: backbone hierarchy rows with release-slice lanes
- roadmap: horizon columns with outcome or initiative grouping
- feature map: standard columns for actor, rules, examples, steps, outcomes, and questions

Rules:

- lane and column labels should come from canonical content, not renderer invention
- empty structural sections may be shown when they are part of a reusable template
- lane, column, and row order should be deterministic
- the layout should make section boundaries obvious without requiring legend hunting

## Grouping and Clustering
Grouping is appropriate when cards belong to a shared stage, theme, actor,
goal, or semantic subsection.

Rules:

- groups should have visible boundaries or headings
- cards should not visually overlap group ownership
- one card should not appear to belong to multiple groups unless canonical content says so
- grouping should reduce ambiguity, not create visual nesting that the schema does not support

## Card and Node Placement
Cards should be placed so the review path is easy to follow and stable over time.

Rules:

- preserve stable card positions where practical during partial updates
- place related cards near their owning section
- avoid decorative diagonal placement or arbitrary scattering
- keep spacing regular enough that users can visually scan the board
- avoid packing cards so tightly that section identity becomes unclear

## Connectors and Relationships
Connectors are optional for board artifacts.

Use them only when the relationship itself is important and readable. Do not
force connectors onto every board.

Rules:

- connectors should clarify dependency, flow, or influence
- connectors must not become the only place where semantic meaning exists
- if connectors are dense enough to reduce readability, prefer stronger grouping instead
- Mermaid should be omitted when the board depends on rich spatial grouping that connectors cannot preserve faithfully

## Template-Generator Rules
Board template generators may intentionally create partially empty canvases.

That is valid when the artifact is a reusable workshop or planning template.

Rules:

- section prompts and blank zones may appear without filled cards
- template structure should still be explicit and reviewable
- empty sections should be purposeful, labeled, and stable
- optional example content must remain clearly separable from the blank template structure

## HTML and Mermaid Guidance
HTML is the default review surface for board artifacts.

Mermaid is optional only when the board can be represented faithfully as a
simple graph or reduced structural view.

Use HTML-only when the board depends on:

- rich spatial grouping
- dense sticky-note style canvases
- matrix-like density inside a board
- multiple simultaneous alignment cues
- workshop layouts where free placement matters

## Layout Metadata Expectations
consistently.

Typical board layout metadata may include:

- orientation
- sections
- lane, column, or row definitions
- grouping metadata
- ordering hints
- card positions or anchors
- spacing or alignment hints

group, or hierarchy element is semantically important, that meaning must also
exist in structured output content.

## Rerender and Update Stability
Board rerenders should preserve the following whenever artifact identity is unchanged:

- section order
- lane, column, and row labels
- stable card identifiers
- unchanged card grouping
- deterministic derivative paths

Partial updates must not silently reorder unrelated sections, relabel unrelated
cards, or collapse stable whitespace and grouping in ways that make review
harder.

## Failure and Clarification Rules
Stop and ask for clarification when any of the following is true:

- the board needs both matrix and board semantics and the dominant structure is unclear
- the request implies a large structural reframe rather than a bounded update
- Mermaid is requested but would clearly lose material meaning
- cards cannot be assigned to sections without guessing
- multiple layout interpretations would lead to different canonical meaning

## Phase-1 Intent
Phase 1 should prefer simple, durable, reviewable board layouts over ambitious
visual styling.

The priority order is:

1. canonical clarity
2. stable grouping
3. deterministic rerendering
4. readable HTML review output
5. optional Mermaid only when fidelity stays high

## Visual Design Integration

Board artifacts use the **Board / Architecture** visual family from `design-system.md`.

### Palette
Apply the terracotta + sage palette tokens. Use `--accent-primary` (terracotta) for primary section headers and key insight cards. Use `--accent-secondary` (sage) for secondary groupings and supporting content.

### Card styling
```css
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 1rem;
  box-shadow: var(--shadow-sm);
  min-width: 0; /* flex shrink safety */
}
.card.hero {
  background: var(--surface-raised);
  border-color: var(--accent-primary);
  box-shadow: var(--shadow-md);
}
.card.recessed {
  background: var(--surface-recessed);
  box-shadow: none;
}
```

### Section headers
```css
.section-header {
  font-family: var(--font-display);
  color: var(--accent-primary);
  border-bottom: 2px solid var(--accent-primary-dim);
  padding-bottom: 0.5rem;
  margin-bottom: 1rem;
}
```

### Background and depth
Apply the dot-grid background from `design-system.md`. Use the three depth tiers (hero, default, recessed) to create visual hierarchy. The guide panel should be `--surface-recessed`, primary content cards should be `--surface`, and key findings should be `--surface-raised` with `--shadow-md`.

### Typography
Use the DM Serif Display + DM Sans pairing. Section headings in `--font-display`, card content in `--font-body`, metadata labels in `--font-mono`.

### Accessibility
Follow `accessibility.md` for all board outputs. Each board section should be a `<section>` or `role="region"` with an `aria-label`. Cards within sections should use semantic list markup.

### Overflow
Board layouts must use the flex/grid safety patterns from `design-system.md`. Wrap boards in a scrollable container when content exceeds viewport width.
