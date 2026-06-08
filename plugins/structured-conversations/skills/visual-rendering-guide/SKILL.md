---
name: visual-rendering-guide
render_family: form
description: "Explain how to visually present structured conversation artifacts as boards, trees, matrices, forms, or flows using HTML or Mermaid. Use when you need layout guidance for rendering discovery, planning, or specification artifacts."
---

# Visual Rendering Guide

Provide guidance on rendering structured conversation artifacts into styled, accessible visual formats.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

## Design System

Read `references/design-system.md` first. It is the single source of truth for:

- **Three visual families** with distinct palettes (terracotta/sage for boards, teal/cyan for Mermaid, rose/cranberry for tables)
- **Dual-theme tokens** (light mode in `:root`, dark mode via `prefers-color-scheme`)
- **Typography** with distinctive font pairings per family
- **Surface depth** with three tiers (hero, default, recessed)
- **Layout resilience** patterns for overflow, flex safety, and scrolling
- **HTML page template** skeleton

## Artifact Type → Visual Family

| Artifact type | Visual family | Palette |
|---|---|---|
| Board, canvas, poster, map | Board / Architecture | Terracotta + sage |
| Tree, flow, graph, process | Mermaid / Flow | Teal + cyan |
| Table, matrix, rubric, comparison | Table / Analytical | Rose + cranberry |

## Renderer Families

Read the relevant layout reference based on the artifact type:

- **Board renderer** — `references/boards/board-layout-rules.md`
- **Tree renderer** — `references/trees/tree-layout-rules.md`
- **Matrix renderer** — `references/matrices/matrix-layout-rules.md`
- **Form renderer** — `references/forms/form-layout-rules.md`
- **Flow renderer** — `references/flows/flow-layout-rules.md`

## Rendering Formats

- **HTML rendering** — `references/visual-rendering-html.md` (default for all visual artifacts)
- **Mermaid rendering** — `references/visual-rendering-mermaid.md` (for trees and flows when faithful)
- **Accessibility** — `references/accessibility.md` (required for all visual outputs)
- **Update rules** — `references/visual-update-rules.md` (when re-rendering)

## Mermaid Requirements

When generating Mermaid diagrams, always:

1. Initialize with `theme: 'base'` and teal/cyan `themeVariables`
2. Include zoom in/out/reset buttons, Ctrl/Cmd+scroll, and click-drag panning
3. Support dark mode via conditional `themeVariables`
4. Quote labels containing punctuation or special characters
5. Split diagrams with more than 20-25 nodes
6. Include a text-alternative table for accessibility

## Accessibility Requirements

Every visual output must meet WCAG 2.1 AA:

- Sufficient text/background contrast (4.5:1 body, 3:1 large text)
- Keyboard navigation with visible focus states
- `prefers-reduced-motion` support
- Semantic HTML structure (`<table>`, `<caption>`, `<th scope>`, headings in order)
- Status indicators use shape + text, not color alone
- Mermaid diagrams include table alternatives

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Visual hierarchy passes the squint test (hero sections dominate, secondary details recede)
- Both dark and light modes are intentionally designed
- Accessibility checklist in `references/accessibility.md` passes
- Structure follows the conventions for this artifact type

## User Experience Contract

- Speak to the user in plain language centered on their goal and the concrete visual being created
- When prerequisites are missing, explain what is needed and suggest the smallest next action
- After generation, explain what the user should review and suggest the most likely next step
