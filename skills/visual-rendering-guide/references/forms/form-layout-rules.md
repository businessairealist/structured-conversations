# Form Layout Rules

## Purpose
This file defines phase-1 layout rules for form and statement artifacts.

Its goal is to keep structured statement-style outputs readable, stable, and
safe for reuse by form-producing skills.

These rules apply to artifacts such as elevator pitches, press releases, epic
statements, defect reports, and OKRI records.

## Scope
This file governs presentation expectations for artifacts whose primary meaning
depends on labeled sections, field structure, and readable narrative order
rather than spatial visualization.

It focuses on section layout, field ordering, prompt structure, and readable
HTML presentation when a rendered view is used. It does not replace the shared
contracts for schema, lifecycle, artifact location, or update integrity.

## Form Artifact Expectations
Form and statement artifacts normally produce the following base outputs:

- the structured markdown output
- the human-readable summary
- optional `outputs/exports/*.docx`
- optional `outputs/exports/*.pdf`

These artifacts are markdown-first by default. They are not required to use the
full visual render package unless the request or workflow clearly needs a
rendered presentation view.

## Core Layout Principles
- Section order should support fast reading and review.
- Labels and prompts should be clearer than decorative styling.
- Field structure should come from canonical content, not renderer invention.
- Unchanged sections should remain stable during updates and rerenders.
- The rendered view should improve readability without changing meaning.

## Preferred Form Structure
Form-style layouts should emphasize:

- title or record heading
- labeled sections or fields
- stable section order
- optional grouped fields when canonical content supports grouping
- clear distinction between completed content and unresolved items

Do not force a statement artifact into a board, tree, or matrix presentation
unless the artifact family genuinely requires that structure.

## Section and Field Rules
Sections should reflect canonical structure directly.

Rules:

- section titles should come from canonical content or explicit family conventions
- required sections should be easy to locate
- optional sections should not visually overpower core content
- field labels should remain stable across rerenders
- long-form sections should preserve readable paragraph structure

## Template and Prompt Rules
Some form artifacts are reusable templates rather than fully populated outputs.

Rules:

- empty prompt fields may be shown when the artifact is intentionally templated
- prompt text should remain clearly separate from filled content
- placeholder content must not be mistaken for canonical factual content
- optional example text should remain distinguishable from the template shell

## HTML Guidance
HTML is optional and request-driven for form artifacts.

Use HTML when it helps with:

- structured review
- side-by-side field reading
- section navigation
- printable or presentation-friendly formatting

Avoid forcing HTML when the human-readable summary already provides the best human-readable
form for the artifact.

## Mermaid Guidance
Mermaid is usually inappropriate for form and statement artifacts.

Mermaid should only be considered when a supporting sub-structure is explicitly
graph-like and separately meaningful. It should not become the main derivative
for a statement artifact.

## Layout Metadata Expectations
If a form artifact uses rendered HTML with layout metadata, that metadata should
remain minimal and presentation-oriented.

Typical metadata may include:

- section ordering hints
- grouped field definitions
- printable layout hints
- optional navigation structure

Semantic field meaning must remain in canonical content rather than only in a
renderer-specific layout file.

## Rerender and Update Stability
Form rerenders should preserve the following whenever artifact identity stays the same:

- stable section order where untouched
- stable field labels
- unchanged narrative content outside the requested update
- deterministic derivative locations

Partial updates must not silently rewrite unrelated sections, change prompt
meaning, or reframe the whole statement under the label of formatting cleanup.

## Failure and Clarification Rules
Stop and ask for clarification when any of the following is true:

- the artifact is actually a matrix, board, or flow in disguise
- required section structure is ambiguous
- the requested change would reframe the whole statement materially
- a rendered view would imply structure not present canonically

## Phase-1 Intent
Phase 1 should treat form artifacts as clarity-first, markdown-first outputs.

The priority order is:

1. section clarity
2. stable field structure
3. readable markdown
4. optional HTML when helpful
5. exports only when requested
