# Rendering Regression Test Specification

Version: 1.0 — introduced with plugin v3.0.2

## Purpose

This specification defines the minimum checks a contributor or reviewer should run after modifying any visual rendering reference, design system token, Mermaid configuration, or layout rule. The goal is to catch regressions before they reach users.

## Scope

Tests cover the three visual families defined in `design-system.md`:

| Family | Palette | Typography | Primary artifacts |
|--------|---------|------------|-------------------|
| Board | Terracotta / Sage | DM Serif / DM Sans | Empathy maps, journey maps, story maps, impact maps |
| Mermaid | Teal / Cyan | Space Grotesk / Space Mono | Trees, flows, sequence diagrams |
| Table | Cranberry / Rose | Source Serif / Source Sans / Source Code | Matrices, comparison tables, scorecards |

---

## Test Cases

### TC-01: Design system tokens load correctly

**Trigger:** Any change to `design-system.md`

1. Generate a board-family HTML artifact (e.g., empathy map builder).
2. Confirm `:root` CSS custom properties are present in the output.
3. Confirm the terracotta accent (`#c05d3b` or equivalent dark-mode value) appears in card headers.
4. Confirm the sage accent (`#6b8f71`) appears in section backgrounds.
5. Confirm Google Fonts `<link>` loads DM Serif Display and DM Sans.

**Pass criteria:** All five checks satisfied. No hardcoded colors outside the token set.

### TC-02: Dark mode switches correctly

**Trigger:** Any change to `design-system.md` or any layout rule file

1. Generate any HTML artifact.
2. View in a browser with `prefers-color-scheme: dark` enabled.
3. Confirm background shifts to the dark surface token (`#1a1a2e` or family equivalent).
4. Confirm text shifts to light tokens (`#e8e0d8` or family equivalent).
5. Confirm accent colors shift to their dark-mode variants.
6. Confirm no white-on-white or dark-on-dark contrast failures.

**Pass criteria:** All elements readable. No flash of light-mode content.

### TC-03: Mermaid diagrams render with custom theme

**Trigger:** Any change to `visual-rendering-mermaid.md`

1. Generate a tree-family artifact that includes a Mermaid diagram.
2. Confirm `mermaid.initialize()` uses `theme: 'base'` with `themeVariables`.
3. Confirm node fills use the teal palette (`#1a8a8a` primary).
4. Confirm edge colors use the cyan accent (`#2bacc2`).
5. Confirm the diagram is wrapped in a container with `role="img"` and `aria-label`.

**Pass criteria:** Diagram renders with custom palette, not Mermaid defaults. Accessibility wrapper present.

### TC-04: Mermaid interaction controls work

**Trigger:** Any change to `visual-rendering-mermaid.md`

1. Generate any Mermaid-containing artifact.
2. Confirm zoom controls (zoom in, zoom out, reset) are rendered.
3. Confirm Ctrl/Cmd + scroll wheel zooms the diagram.
4. Confirm click-drag pans the diagram.
5. Confirm the reset button restores the original view.

**Pass criteria:** All four interaction modes functional. Controls styled consistently with the design system.

### TC-05: Table family renders with semantic HTML

**Trigger:** Any change to `matrix-layout-rules.md`

1. Generate a matrix-family artifact (e.g., pitch comparison matrix).
2. Confirm the output uses `<table>`, `<thead>`, `<tbody>`, `<th scope="col">`.
3. Confirm sticky header CSS is present (`position: sticky; top: 0`).
4. Confirm alternating row shading uses the rose palette.
5. Confirm numeric cells are right-aligned with monospace font.

**Pass criteria:** Semantic table structure. Visual styling matches table family tokens.

### TC-06: Board layout resilience

**Trigger:** Any change to `board-layout-rules.md`

1. Generate a board artifact with 8+ cards in a single section.
2. Confirm cards wrap using `flex-wrap: wrap` without horizontal overflow.
3. Confirm each card has `min-width: 0` to prevent flex blowout.
4. Confirm long text content inside cards truncates or wraps gracefully.
5. Resize the viewport to 360px width; confirm no horizontal scrollbar on the page body.

**Pass criteria:** No overflow at any viewport width. Cards remain readable at mobile size.

### TC-07: Accessibility — contrast ratios

**Trigger:** Any change to `design-system.md` or `accessibility.md`

1. Generate one artifact from each family (board, Mermaid, table).
2. For each, check body text contrast against its background (target: ≥ 4.5:1).
3. Check heading/large text contrast (target: ≥ 3:1).
4. Check interactive element (link, button) contrast (target: ≥ 3:1).
5. Repeat all checks in dark mode.

**Pass criteria:** All ratios meet WCAG 2.1 AA minimums in both modes.

### TC-08: Accessibility — keyboard navigation

**Trigger:** Any change to `accessibility.md` or any layout rule file

1. Generate an artifact with interactive elements (e.g., Mermaid controls, expandable sections).
2. Tab through all interactive elements.
3. Confirm visible focus indicator on each (`:focus-visible` outline).
4. Confirm logical tab order (left-to-right, top-to-bottom).
5. Confirm no keyboard traps.

**Pass criteria:** All interactive elements reachable and operable by keyboard alone.

### TC-09: Accessibility — reduced motion

**Trigger:** Any change to `accessibility.md` or `design-system.md`

1. Generate any artifact.
2. Enable `prefers-reduced-motion: reduce` in browser settings.
3. Confirm all CSS transitions and animations are suppressed.
4. Confirm Mermaid diagram still renders (just without animated transitions).

**Pass criteria:** No motion when reduced-motion is active.

### TC-10: Cross-family consistency

**Trigger:** Any change that touches more than one family's references

1. Generate one artifact from each family in the same session.
2. Confirm surface depth tiers (hero, default, recessed) use consistent shadow values across families.
3. Confirm spacing scale is consistent (the same `--space-*` tokens).
4. Confirm the dot-grid background pattern renders identically across families.

**Pass criteria:** Shared design system tokens produce identical results regardless of family.

### TC-11: Font loading graceful degradation

**Trigger:** Any change to `design-system.md`

1. Generate any artifact.
2. Block Google Fonts loading (e.g., disconnect network or block the domain).
3. Confirm the artifact still renders with fallback fonts (`Georgia`, `system-ui`, `Consolas`).
4. Confirm no layout shift or broken rendering from missing fonts.

**Pass criteria:** Artifact is fully usable with fallback fonts.

### TC-12: No ghost pipeline references

**Trigger:** Any change to any SKILL.md or reference file

1. Search all SKILL.md files for: `scripts/`, `render/html/`, `layout.json`, `register_artifact`, `write_run_manifest`, `artifact.json`, `project.folder`, `runs/manifests`.
2. Search all reference files for the same patterns.
3. Confirm zero matches.

**Pass criteria:** Zero ghost pipeline references across the entire plugin.

---

## Running Tests

These tests are manual verification checks. To run them:

1. Load the plugin in a Claude/Cowork session.
2. Invoke the relevant skill to generate an artifact.
3. Open the generated HTML file in a browser.
4. Apply each check from the relevant test case.

For TC-12 (ghost pipeline), use grep:
```bash
grep -rn "scripts/\|render/html/\|layout\.json\|register_artifact\|write_run_manifest\|artifact\.json\|project\.folder\|runs/manifests" skills/ references/
```

## Maintenance

When adding a new visual family or layout type, add a corresponding test case. When modifying an existing test case, update the version number at the top of this file.
