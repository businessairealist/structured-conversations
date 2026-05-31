# Matrix Layout Rules

## Purpose
This file defines phase-1 layout rules for matrix artifacts.

Its goal is to keep row-column visuals precise, readable, and stable across
rerenders for matrix-producing skills.

These rules apply to artifacts such as comparison matrices, prioritization
matrices, rule-example tables, and rubric-based analysis.

## Scope
This file governs arrangement and review expectations for artifacts whose
primary meaning depends on rows, columns, headers, and cell content.

It focuses on grid structure, header clarity, cell density, ordering, and
render stability. It does not replace the shared contracts for schema,
lifecycle, artifact location, or update integrity.

## Matrix Artifact Expectations
Matrix artifacts normally produce the following package:

- the structured markdown output
- the human-readable summary
- optional `outputs/exports/*.csv`

HTML is expected. Mermaid is optional and usually inappropriate for dense,
tabular, scored, or comparison-heavy matrices.

## Core Layout Principles
- Row and column meaning must be obvious.
- Header structure should dominate over decorative styling.
- Cell alignment must support comparison, not frustrate it.
- Unchanged rows, columns, and cells should remain stable during updates.
- Dense matrices should remain scannable without losing fidelity.
- Sorting and ordering should be deterministic.

## Preferred Matrix Structure
Matrix layouts should emphasize:

- column headers
- row headers or row identifiers
- stable cell boundaries
- optional grouped headers when canonical content defines them
- consistent alignment within a column

Do not collapse a true matrix into a board or flow layout just for visual
variety. The grid is the core review structure.

## Header Rules
Headers carry primary review meaning and should be easy to find.

Rules:

- column headers should remain visible and distinct
- row labels should remain visually tied to their row content
- grouped headers should only appear when canonical content supports them
- header wording should come from canonical content, not renderer invention

## Row and Column Ordering
Order should be deterministic and reviewable.

Rules:

- row order should reflect canonical ordering or explicit sort rules
- column order should reflect semantic importance, workflow order, or canonical structure
- rerenders should not silently reorder rows or columns without a semantic reason
- stable row and column identifiers should be preserved where applicable

## Cell Layout Rules
Cells should preserve comparison fidelity.

Rules:

- cell boundaries should remain visually clear
- text-heavy cells should wrap predictably instead of overflowing unpredictably
- numeric or scored columns should align consistently
- multi-value cells should be structured in a stable way
- blank cells should be visually distinguishable from missing or invalid data when that distinction matters

## Density Rules
Matrix artifacts often carry a lot of information.

Rules:

- prefer readable density over ornamental spacing
- avoid collapsing columns so far that comparison becomes difficult
- use HTML as the primary review surface when the matrix is dense
- use CSV exports only as derivatives, not as the canonical source of meaning

## HTML and Mermaid Guidance
HTML is the default review surface for matrix artifacts.

Mermaid should be generated only when the matrix can be reduced to a faithful
simple structure without losing important row-column meaning.

Mermaid should usually be omitted when the matrix depends on:

- dense tabular comparison
- scoring or weighting
- multiple long text columns
- complex grouped headers
- precise cell-by-cell review

## Layout Metadata Expectations
matrix consistently.

Typical fields may include:

- column definitions
- row grouping
- header grouping
- ordering hints
- width or sizing hints
- alignment preferences

Any semantically important row or column structure must also exist in canonical

## Rerender and Update Stability
Matrix rerenders should preserve the following whenever artifact identity stays the same:

- stable row order where untouched
- stable column order where untouched
- unchanged cell content outside the requested update
- deterministic derivative locations
- stable row or column identifiers when applicable

Partial updates must not silently rewrite neighboring cells, reorder unrelated
rows, or change header structure unless the requested change logically requires it.

## Failure and Clarification Rules
Stop and ask for clarification when any of the following is true:

- the artifact mixes matrix and board semantics and the dominant model is unclear
- row or column identity is ambiguous
- the requested update implies a structural grid rewrite
- Mermaid would materially reduce matrix fidelity
- multiple header interpretations would lead to different review outcomes

## Phase-1 Intent
Phase 1 should treat matrix clarity as more important than visual flourish.

The priority order is:

1. header clarity
2. comparison fidelity
3. stable ordering
4. readable HTML
5. optional Mermaid only when the matrix can be faithfully simplified

## Visual Design Integration

Matrix artifacts use the **Table / Analytical** visual family from `design-system.md`.

### Palette
Apply the rose + cranberry palette tokens. Use `--accent-primary` (cranberry) for column headers and key metrics. Use semantic status colors (`--accent-pass`, `--accent-fail`, `--accent-warn`, `--accent-info`) for status indicators.

### Semantic HTML table template
Every data table must use proper semantic HTML:

```html
<div class="table-container"> <!-- overflow safety -->
  <table>
    <caption>Descriptive table title</caption>
    <thead>
      <tr>
        <th scope="col">Column 1</th>
        <th scope="col">Column 2</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row">Row header</th>
        <td>Cell value</td>
      </tr>
    </tbody>
  </table>
</div>
```

### Sticky header
```css
thead th {
  position: sticky;
  top: 0;
  background: var(--surface-raised);
  z-index: 2;
  border-bottom: 2px solid var(--accent-primary);
  font-family: var(--font-display);
  color: var(--accent-primary);
}
```

### Alternating rows and hover
```css
tbody tr:nth-child(even) { background: var(--surface-recessed); }
tbody tr:hover { background: color-mix(in srgb, var(--accent-secondary) 10%, var(--surface)); }
```

### Status indicators
Status cells must use shape + text + color (never color alone):

```css
.status { 
  display: inline-flex; align-items: center; gap: 0.25rem;
  font-family: var(--font-mono); font-size: 0.8rem;
  padding: 0.15rem 0.5rem; border-radius: 4px;
}
```

See `accessibility.md` for the full status indicator pattern.

### Numeric alignment
Right-align numeric columns using `text-align: right` on both `<th>` and `<td>` for those columns. Use tabular-nums for consistent digit width:

```css
td.numeric, th.numeric {
  text-align: right;
  font-variant-numeric: tabular-nums;
  font-family: var(--font-mono);
}
```

### Overflow
Wide tables must be horizontally scrollable. Wrap in `.table-container` with `overflow-x: auto`.

### Typography
Use Source Serif 4 + Source Sans 3 pairing. Column headers in `--font-display`, cell content in `--font-body`, numeric values and labels in `--font-mono`.
