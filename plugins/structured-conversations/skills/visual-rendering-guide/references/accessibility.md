# Accessibility Standards

## Purpose

This file defines the accessibility requirements for all HTML and Mermaid outputs produced by structured conversation skills. The target quality level is WCAG 2.1 AA.

## Contrast Requirements

All text and interactive elements must meet minimum contrast ratios against their backgrounds.

| Element type | Minimum contrast ratio |
|---|---|
| Body text | 4.5:1 |
| Large text (18px+ or 14px+ bold) | 3:1 |
| UI components and graphical objects | 3:1 |
| Focus indicators | 3:1 against adjacent colors |

### Verification

Use the design system tokens from `design-system.md`. The defined palettes are designed to meet these ratios, but verify when combining accent colors with non-standard backgrounds:

```
Acceptable:  var(--text) on var(--surface)        → high contrast
Acceptable:  var(--text-dim) on var(--surface)     → meets 4.5:1
Check first: var(--text-muted) on var(--surface)   → verify 4.5:1
Avoid:       var(--text-muted) on colored accent   → likely fails
```

## Semantic HTML Structure

All generated HTML must use semantic elements correctly:

### Page structure
```html
<html lang="en">
<main> <!-- primary content -->
<nav>  <!-- navigation if needed -->
<header>, <footer>, <section>, <article> <!-- as appropriate -->
```

### Headings
- Use a single `<h1>` for the artifact title
- Use `<h2>` through `<h4>` in order — never skip levels
- Headings must describe the content that follows

### Tables
```html
<table>
  <caption>Descriptive title for the table</caption>
  <thead>
    <tr>
      <th scope="col">Column header</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Row header (if applicable)</th>
      <td>Cell content</td>
    </tr>
  </tbody>
</table>
```

### Lists
- Use `<ul>` for unordered lists, `<ol>` for ordered lists
- Never use lists for layout — use CSS grid or flex instead

## Keyboard Navigation

All interactive elements must be keyboard accessible:

### Focus order
- Follow the visual reading order (typically left-to-right, top-to-bottom)
- Do not use positive `tabindex` values — use the natural DOM order
- Ensure no elements trap keyboard focus

### Focus visibility
Every focusable element must show a visible focus indicator:

```css
:focus-visible {
  outline: 2px solid var(--accent-primary);
  outline-offset: 2px;
  border-radius: 4px;
}

/* Remove outline for mouse clicks but keep for keyboard */
:focus:not(:focus-visible) {
  outline: none;
}
```

### Interactive controls
- Buttons must be `<button>` elements (not `<div>` or `<span>`)
- Custom controls must have `role`, `aria-label`, and keyboard event handlers
- Mermaid zoom/pan/reset buttons must be keyboard accessible

## ARIA Attributes

Use ARIA only when native HTML semantics are insufficient:

### Common patterns

**Status indicators:**
```html
<span class="status pass" role="img" aria-label="Pass">&#x2713; Pass</span>
<span class="status fail" role="img" aria-label="Fail">&#x2717; Fail</span>
<span class="status warn" role="img" aria-label="Warning">&#x26A0; Warn</span>
```

**Diagram containers:**
```html
<figure role="figure" aria-label="Impact map: Increase retention by 15%">
  <div class="mermaid-wrapper">
    <!-- Mermaid diagram -->
  </div>
  <figcaption class="sr-only">Impact map showing goal, actors, impacts, and deliverables</figcaption>
</figure>
```

**Cards on boards:**
```html
<div role="region" aria-label="Hear section">
  <h3>Hear</h3>
  <ul>
    <li>"We keep getting the same complaint" — Support ticket #412</li>
  </ul>
</div>
```

## Reduced Motion

Respect the user's motion preference. Disable all non-essential animation when `prefers-reduced-motion: reduce` is active:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### What counts as non-essential
- Staggered card reveal animations
- Hover scale/shadow transitions
- Loading spinners (replace with static text)
- Parallax effects

### What may remain
- Focus indicator transitions (keep instant)
- Essential state changes (e.g., expanding/collapsing sections)

## Chart and Diagram Alternatives

Every Mermaid diagram or visual chart must include a text-based alternative for screen readers:

### Strategy 1: Summary + table (preferred for complex diagrams)

```html
<figure>
  <div class="mermaid-wrapper">
    <!-- Mermaid diagram -->
  </div>
  <details>
    <summary>View as text table</summary>
    <table>
      <caption>Impact map: Increase retention by 15%</caption>
      <thead>
        <tr><th scope="col">Level</th><th scope="col">Node</th><th scope="col">Parent</th></tr>
      </thead>
      <tbody>
        <tr><td>Goal</td><td>Increase retention by 15%</td><td>—</td></tr>
        <tr><td>Actor</td><td>Free-tier users</td><td>Goal</td></tr>
        <!-- ... -->
      </tbody>
    </table>
  </details>
</figure>
```

### Strategy 2: Screen-reader-only description (for simple diagrams)

```html
<figure aria-label="Hypothesis tree">
  <div class="mermaid-wrapper"><!-- diagram --></div>
  <div class="sr-only">
    Observation: Checkout abandonment increased 12% this month.
    Hypothesis 1: New shipping calculator is confusing.
    Hypothesis 2: Payment form errors increased after deploy.
  </div>
</figure>
```

### Screen-reader-only utility class

```css
.sr-only {
  position: absolute;
  width: 1px; height: 1px;
  padding: 0; margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

## Color Independence

Status indicators must never rely on color alone. Always combine color with shape, text, or icon:

| Status | Color | Shape/text |
|---|---|---|
| Pass | Green (`--accent-pass`) | Checkmark &#x2713; + "Pass" text |
| Fail | Red (`--accent-fail`) | Cross &#x2717; + "Fail" text |
| Warning | Amber (`--accent-warn`) | Triangle &#x26A0; + "Warn" text |
| Info | Blue (`--accent-info`) | Circle &#x24D8; + "Info" text |

```css
.status { 
  display: inline-flex; align-items: center; gap: 0.25rem;
  font-family: var(--font-mono); font-size: 0.8rem;
  padding: 0.15rem 0.5rem; border-radius: 4px;
}
.status.pass { background: color-mix(in srgb, var(--accent-pass) 15%, transparent); color: var(--accent-pass); }
.status.fail { background: color-mix(in srgb, var(--accent-fail) 15%, transparent); color: var(--accent-fail); }
.status.warn { background: color-mix(in srgb, var(--accent-warn) 15%, transparent); color: var(--accent-warn); }
.status.info { background: color-mix(in srgb, var(--accent-info) 15%, transparent); color: var(--accent-info); }
```

## Checklist

Before delivering any HTML or Mermaid output, verify:

- [ ] `<html lang="en">` is set
- [ ] Heading hierarchy is correct (no skipped levels)
- [ ] All images and icons have `alt` text or `aria-label`
- [ ] Tables use `<caption>`, `<thead>`, `<th scope>`
- [ ] Color contrast meets 4.5:1 for body text
- [ ] Interactive controls are keyboard accessible
- [ ] Focus indicators are visible
- [ ] `prefers-reduced-motion` is respected
- [ ] Mermaid diagrams have a text alternative
- [ ] Status indicators use shape/text, not color alone
