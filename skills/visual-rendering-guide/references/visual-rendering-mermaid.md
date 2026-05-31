# Visual Rendering: Mermaid

## Purpose

This file defines how to configure, style, and present Mermaid diagrams in structured conversation artifacts. It covers initialization, theming, interaction controls, robustness rules, and dark mode support.

## When to Use Mermaid

Mermaid is appropriate for artifacts whose dominant structure can be represented faithfully as a directed graph, tree, or flow:

- Impact maps (goal → actors → impacts → deliverables)
- Hypothesis trees (observation → hypotheses → experiments → decisions)
- Opportunity-solution trees (outcome → opportunities → solutions → experiments)
- Process flows and value stream maps
- Simple dependency graphs

## When to Omit Mermaid

Omit Mermaid and use HTML instead when the artifact depends on:

- Dense sticky-note board layouts (empathy maps, journey maps)
- Rich spatial grouping that connectors cannot preserve
- Heavy tabular content (comparison matrices, scoring rubrics)
- Precise placement, density, or layered annotations
- Workshop canvases where free placement matters

Omitting Mermaid is better than shipping a misleading or unreadable diagram.

## Initialization

Always initialize Mermaid with `theme: 'base'` and custom `themeVariables` from the teal/cyan palette family:

```javascript
mermaid.initialize({
  startOnLoad: true,
  theme: 'base',
  themeVariables: {
    // Node styling
    primaryColor: '#e6f5f5',
    primaryBorderColor: '#1a8a8a',
    primaryTextColor: '#1e2d30',

    // Secondary nodes
    secondaryColor: '#e0f0f5',
    secondaryBorderColor: '#2bacc2',
    secondaryTextColor: '#1e2d30',

    // Tertiary / accent
    tertiaryColor: '#fef5e0',
    tertiaryBorderColor: '#c49a2a',
    tertiaryTextColor: '#2e2200',

    // Lines and edges
    lineColor: '#4a6268',
    textColor: '#1e2d30',

    // Fonts
    fontFamily: "'Space Grotesk', 'Helvetica Neue', sans-serif",
    fontSize: '14px',

    // Background
    background: '#f5fafb',
  },
  flowchart: {
    curve: 'basis',
    padding: 16,
    htmlLabels: true,
  },
  look: 'handDrawn',  // Use hand-drawn style where it improves communication
});
```

### Dark mode initialization

Detect the user's preference and apply dark-mode variables:

```javascript
const isDark = window.matchMedia('(prefers-color-scheme: dark)').matches;

mermaid.initialize({
  startOnLoad: true,
  theme: 'base',
  themeVariables: isDark ? {
    primaryColor: '#1e3838',
    primaryBorderColor: '#30a8a8',
    primaryTextColor: '#dce8ea',
    secondaryColor: '#1a3040',
    secondaryBorderColor: '#40c0d6',
    secondaryTextColor: '#dce8ea',
    tertiaryColor: '#2a2810',
    tertiaryBorderColor: '#d4aa3a',
    tertiaryTextColor: '#e8e0c0',
    lineColor: '#9ab4b8',
    textColor: '#dce8ea',
    fontFamily: "'Space Grotesk', 'Helvetica Neue', sans-serif",
    fontSize: '14px',
    background: '#141e20',
  } : {
    // ... light-mode variables as above
  },
  look: 'handDrawn',
});
```

## Mandatory Interaction Controls

Every page that contains a Mermaid diagram must include zoom, pan, and reset controls. This is required because large trees and flows become unreadable at default scale.

### Required controls

1. **Zoom in button** (+)
2. **Zoom out button** (-)
3. **Reset button** (fit to view)
4. **Ctrl/Cmd + mouse wheel** zoom
5. **Click-and-drag** panning
6. **Cursor states:** `grab` at rest, `grabbing` while dragging

### Implementation

Wrap each Mermaid diagram in a container and apply the controls:

```html
<div class="mermaid-wrapper">
  <div class="mermaid-controls">
    <button onclick="zoomIn(this)" title="Zoom in">+</button>
    <button onclick="zoomOut(this)" title="Zoom out">-</button>
    <button onclick="resetZoom(this)" title="Reset zoom">Reset</button>
  </div>
  <div class="mermaid-viewport" style="overflow: hidden; cursor: grab;">
    <div class="mermaid-content" style="transform-origin: 0 0;">
      <pre class="mermaid">
        graph LR
          A[Start] --> B[End]
      </pre>
    </div>
  </div>
</div>
```

```javascript
function initMermaidControls() {
  document.querySelectorAll('.mermaid-viewport').forEach(viewport => {
    const content = viewport.querySelector('.mermaid-content');
    let scale = 1, panX = 0, panY = 0, isPanning = false, startX, startY;

    function applyTransform() {
      content.style.transform = `translate(${panX}px, ${panY}px) scale(${scale})`;
    }

    // Mouse wheel zoom (Ctrl/Cmd + scroll)
    viewport.addEventListener('wheel', e => {
      if (e.ctrlKey || e.metaKey) {
        e.preventDefault();
        const delta = e.deltaY > 0 ? 0.9 : 1.1;
        scale = Math.max(0.1, Math.min(5, scale * delta));
        applyTransform();
      }
    }, { passive: false });

    // Click-drag panning
    viewport.addEventListener('mousedown', e => {
      isPanning = true;
      startX = e.clientX - panX;
      startY = e.clientY - panY;
      viewport.style.cursor = 'grabbing';
    });
    window.addEventListener('mousemove', e => {
      if (!isPanning) return;
      panX = e.clientX - startX;
      panY = e.clientY - startY;
      applyTransform();
    });
    window.addEventListener('mouseup', () => {
      isPanning = false;
      viewport.style.cursor = 'grab';
    });
  });
}

function zoomIn(btn) {
  const vp = btn.closest('.mermaid-wrapper').querySelector('.mermaid-content');
  const current = parseFloat(vp.style.transform.match(/scale\(([\d.]+)\)/)?.[1] || 1);
  vp.style.transform = vp.style.transform.replace(/scale\([\d.]+\)/, `scale(${Math.min(5, current * 1.2)})`);
}

function zoomOut(btn) {
  const vp = btn.closest('.mermaid-wrapper').querySelector('.mermaid-content');
  const current = parseFloat(vp.style.transform.match(/scale\(([\d.]+)\)/)?.[1] || 1);
  vp.style.transform = vp.style.transform.replace(/scale\([\d.]+\)/, `scale(${Math.max(0.1, current / 1.2)})`);
}

function resetZoom(btn) {
  const vp = btn.closest('.mermaid-wrapper').querySelector('.mermaid-content');
  vp.style.transform = 'translate(0px, 0px) scale(1)';
}

// Initialize after Mermaid renders
mermaid.run().then(() => initMermaidControls());
```

### Control styling

```css
.mermaid-wrapper { position: relative; margin: 1.5rem 0; }
.mermaid-controls {
  display: flex; gap: 0.25rem;
  position: absolute; top: 0.5rem; right: 0.5rem; z-index: 10;
}
.mermaid-controls button {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 6px; padding: 0.25rem 0.75rem;
  font-family: var(--font-mono); font-size: 0.85rem;
  color: var(--text); cursor: pointer;
}
.mermaid-controls button:hover {
  background: var(--surface-raised); border-color: var(--accent-primary);
}
.mermaid-viewport {
  border: 1px solid var(--border); border-radius: 8px;
  background: var(--surface); min-height: 200px;
  overflow: hidden;
}
```

## Label and ID Rules

- **Quote labels** containing punctuation, special characters, or spaces: `A["User clicks 'Submit'"]`
- **Keep IDs** simple, alphanumeric, and stable: `A`, `node1`, `actorBuyer` — not UUIDs
- **Avoid oversized graphs.** If a diagram has more than 20-25 nodes, split it into sub-diagrams with clear scope boundaries and cross-references

## Diagram Types by Artifact

| Artifact | Mermaid type | Direction |
|---|---|---|
| Impact map | `graph LR` | Left to right |
| Hypothesis tree | `graph TD` | Top to bottom |
| Opportunity-solution tree | `graph TD` | Top to bottom |
| Process flow | `flowchart LR` | Left to right |
| Value stream | `flowchart LR` | Left to right |
| Decision tree | `graph TD` | Top to bottom |
| Dependency graph | `graph LR` | Left to right |

## Mermaid + HTML Coexistence

When a Mermaid diagram appears on an HTML page:

1. Load the Mermaid library: `<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>`
2. Load the Space Grotesk font family
3. Use the teal/cyan CSS tokens from `design-system.md` for the page wrapper
4. Place the Mermaid container inside a `.mermaid-wrapper` with controls
5. Include a table-based text alternative for accessibility (see `accessibility.md`)

## Stability

- Equivalent canonical inputs should produce materially equivalent Mermaid structure
- Untouched branches or steps should not be rearranged during partial updates
- Labels must remain stable when content is unchanged
- Do not invent missing connectors, branches, or hierarchy
