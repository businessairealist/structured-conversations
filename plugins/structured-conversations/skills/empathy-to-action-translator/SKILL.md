---
name: empathy-to-action-translator
render_family: board
description: Translate a completed empathy map into a downstream action artifact. Use when you need to turn empathy-map evidence into action-oriented goals, opportunity areas, journey hypotheses, and story seeds that can feed impact maps, journey maps, stories, or roadmap planning.
---

# Empathy To Action Translator

Transform a completed empathy map into a downstream action artifact that preserves traceability to the upstream evidence.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- A completed empathy map or structured empathy evidence that can be resolved into one.
## Structure The Translation

Preserve the upstream actor context and translate empathy signals into downstream-ready sections.

The current implementation writes four action-oriented sections:

- `goals`: verb-plus-noun style improvement goals derived from empathy-map signals
- `opportunities`: intervention areas worth exploring
- `journey-hypotheses`: flow or friction hypotheses that can feed journey work
- `story-seeds`: early story or delivery seeds that still require refinement

For each generated item:

- keep the originating empathy signal or evidence text,
- preserve source references back to the empathy map,
- mark inference clearly when the translated action is interpretive,
- avoid presenting heuristic output as delivery-ready commitment.

## Related Skills

Use these adjacent skills when the request points beyond translation:

- `verb-noun-rewriter` when the goals need clearer action phrasing.
- `syntax-pattern-selector` when the output needs a more specific language frame.
- `empathy-map-builder` when no upstream empathy map exists yet.
- `impact-map-builder` when the translated action seeds should be organized into an impact map next.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. A single-file HTML page rendering the artifact in its board layout (zones, lanes, cards, or spatial groupings). Use clean semantic HTML with a light/dark-friendly palette.
3. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`, `checkout-flow-empathy-map.html`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

