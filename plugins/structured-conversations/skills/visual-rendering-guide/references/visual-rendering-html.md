# Visual Rendering: HTML

## Purpose

This file defines how to generate HTML pages for structured conversation artifacts. HTML is the default high-fidelity visual output format.

## When to Use HTML

HTML is the default visual render target. Use it for all artifact types unless the output is purely textual (markdown-only form artifacts). HTML is especially preferred for:

- Dense board layouts (empathy maps, journey maps, story maps)
- Rich spatial grouping
- Matrix and table content
- Any artifact requiring precise visual hierarchy
- Workshop canvases and poster-style layouts

## Required Resources

Every HTML page must reference:

1. **`design-system.md`** — for the correct palette family, theme tokens, typography, surface depth, and overflow patterns
2. **`accessibility.md`** — for WCAG 2.1 AA compliance, semantic structure, focus states, and reduced motion

## Design System Integration

### Step 1: Choose the visual family

| Artifact type | Family | Reference |
|---|---|---|
| Board / canvas / poster | Terracotta + sage | `design-system.md` Board section |
| Directed graph / tree / flow | Teal + cyan | `design-system.md` Mermaid section |
| Data table / matrix / rubric | Rose + cranberry | `design-system.md` Table section |

### Step 2: Apply the HTML page template

Use the full page skeleton from `design-system.md`, including:

- `<html lang="en">` for accessibility
- `<meta name="viewport">` for responsiveness
- Google Fonts `<link>` for the chosen family
- CSS custom properties in `:root` for light mode
- `@media (prefers-color-scheme: dark)` overrides for dark mode
- `@media (prefers-reduced-motion: reduce)` for motion safety
- Dot-grid background pattern
- Base reset and typography styles

### Step 3: Apply depth tiers

Use the three surface tiers from `design-system.md`:

- **Hero / elevated** for primary insights, key findings, title sections
- **Default** for standard content cards and sections
- **Recessed** for metadata, secondary details, and code/evidence blocks

### Step 4: Verify accessibility

Before delivering, run through the checklist in `accessibility.md`:

- Heading hierarchy, semantic structure, contrast, focus states, color independence, reduced motion, alternatives for charts

## Structure Rules

HTML output should expose the dominant artifact structure clearly:

- **Boards:** sections, lanes, clusters, cards
- **Trees:** levels, branches, connectors, node groups (or Mermaid with controls)
- **Matrices:** headers, rows, columns, cells with semantic table markup
- **Flows:** steps, direction, branches, joins, lanes (or Mermaid with controls)
- **Forms:** sections, fields, prompts, narrative blocks

The visible structure must match the artifact family instead of flattening everything into one generic layout.

## Readability Rules

- Labels must remain legible at normal viewing sizes
- Dense content must wrap or scroll predictably (use overflow patterns from `design-system.md`)
- Grouping boundaries must be visually obvious
- The dominant reading path must be easy to follow
- Decorative effects must not reduce clarity

## Stability Rules

- Equivalent inputs should produce materially equivalent HTML structure
- Untouched sections must not be silently reformatted during updates
- Re-rendering should not reorder unrelated structures without a semantic reason

## Relationship to Other References

- `design-system.md` — palette families, theme tokens, typography, depth, overflow patterns
- `accessibility.md` — WCAG compliance, semantic HTML, focus, motion, alternatives
- `visual-rendering-mermaid.md` — Mermaid configuration when diagrams coexist with HTML
- `boards/board-layout-rules.md` — board-specific structure and styling
- `trees/tree-layout-rules.md` — tree-specific structure and Mermaid integration
- `matrices/matrix-layout-rules.md` — table structure, sticky headers, status indicators
- `flows/flow-layout-rules.md` — flow structure and direction rules
- `forms/form-layout-rules.md` — form section layout and field structure
