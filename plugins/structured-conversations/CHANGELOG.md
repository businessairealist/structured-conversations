# Changelog

All notable changes to the Structured Conversations plugin are documented here.

## [3.0.3] - 2026-05-30

### Render Family Metadata (F3)

- Added `render_family` field to all 95 SKILL.md frontmatters — board (30), form (26), matrix (20), plan (8), tree (7), flow (3), scenario (1)
- Agents no longer need to infer the artifact family from prose; the family is now explicit and machine-readable in frontmatter

### HTML Render Instructions (F2)

- Added explicit HTML rendering step to the Write Outputs section of all 40 board, tree, and flow family skills
- Board skills instruct: single-file HTML with zones, lanes, cards, and spatial groupings
- Tree skills instruct: single-file HTML with collapsible parent-child hierarchy
- Flow skills instruct: single-file HTML with directional steps, swim lanes, or sequences
- Matrix, form, plan, and scenario families remain markdown-first (55 skills unchanged) — HTML available on request only

## [3.0.2] - 2026-04-26

### Visual Rendering System

- **Ghost pipeline removal (P0):** Stripped all Codex-era rendering pipeline references from 72 SKILL.md files and 45 reference files — removed `scripts/`, `render/html/`, `layout.json`, `register_artifact`, `write_run_manifest`, artifact registry, and run manifest patterns
- **Rewrote `project-folder-contract.md`** from Codex infrastructure contract to concise Claude/Cowork workspace conventions
- **Created `design-system.md`** (408 lines): single source of truth for all visual styling — three palette families (board/terracotta+sage, Mermaid/teal+cyan, table/cranberry+rose), surface depth tiers, shadow system, typography with Google Fonts, dark mode via `prefers-color-scheme`, full HTML page template skeleton
- **Rewrote `visual-rendering-mermaid.md`** (258 lines): complete Mermaid configuration with `theme: 'base'` + custom `themeVariables`, dark mode initialization, zoom/pan/reset interaction controls with JavaScript, label quoting and diagram sizing rules
- **Created `accessibility.md`** (247 lines): WCAG 2.1 AA compliance — contrast ratios, semantic HTML patterns, keyboard navigation with `:focus-visible`, ARIA patterns, `prefers-reduced-motion` support, chart text alternatives, `.sr-only` utility class

### Layout Rule Updates (P1)

- **Board layout rules:** Added Visual Design Integration section — card CSS with design system tokens, section headers, depth guidance, typography, accessibility, overflow handling
- **Tree layout rules:** Added Visual Design Integration section — Mermaid palette reference, node styling by level, HTML fallback tree, accessibility
- **Matrix layout rules:** Added Visual Design Integration section — semantic HTML table template, sticky headers, alternating rows with rose palette, status indicators, numeric alignment
- **Rewrote `visual-rendering-html.md`** to integrate design system, accessibility, and family-specific reference dispatch
- **Rewrote `visual-rendering-guide/SKILL.md`** with design system mapping table, Mermaid requirements, accessibility requirements, and references to all new files

### Consolidation (P2)

- Filled 44 empty `## Write Outputs` placeholder sections with standard output guidance
- Removed 8 redundant standalone `## Output` sections (ghost content from Codex era)
- Created `rendering-test-spec.md`: 12 regression test cases covering design tokens, dark mode, Mermaid rendering, accessibility, cross-family consistency, and ghost pipeline detection

## [3.0.1] - 2026-04-26

### Descriptions
- Rewrote 25 skill descriptions to remove tautological "This skill should be used when the user wants to [skill name]" pattern
- All 25 now lead with an imperative verb, state the input-to-output transformation, and end with a "Use whe