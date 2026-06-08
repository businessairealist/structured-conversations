# Visual Update Rules

## Purpose
This file defines phase-1 update rules for visual artifacts.

Its goal is to preserve semantic integrity, layout trustworthiness, and
rerender stability when board, tree, matrix, flow, or rendered form artifacts
are updated.

## Scope
This file governs how visual artifacts should be changed after the correct
target artifact has already been selected.

It applies to canonical updates, layout-only updates, rerendering behavior, and
update recording for visual derivatives.

## Core Update Contract
- the structured markdown output must be updated first for any canonical semantic change.
- Only the requested fields, nodes, cards, branches, rows, sections, or metadata may change.
- Unchanged visual structures must be preserved whenever the artifact remains the same artifact.
- HTML, Mermaid, SVG, PNG, and other renders are derivatives, not the primary editable source.
- Rerendering must not introduce unrelated structural drift.

## Allowed Update Classes
Visual artifacts may receive the following kinds of updates:

- metadata-only updates
- bounded content updates preserving identity
- layout-only derivative updates
- semantic updates preserving identity

If a requested change would materially reframe the artifact, change its
semantic scope, or hide a major replacement inside the same identity, it should
be treated as clarification-required or as a superseding artifact instead.

## Preserve-Unchanged-Content Rules
The following should remain stable unless explicitly targeted:

- stable node, card, row, column, branch, or section identifiers
- untouched semantic content
- provenance and upstream traceability
- deterministic derivative locations
- stable section, lane, or branch order where not semantically changed

An update must not rewrite unrelated content just because the artifact was
reopened or rerendered.

## Layout-Only Update Rules
Layout-only changes are valid only when they do not change semantic meaning.

Examples:

- spacing adjustments
- anchor repositioning
- lane width adjustments
- header sizing
- visual alignment cleanup

Rules:

- semantic content in the structured markdown output must remain unchanged
- stable element IDs must be preserved
- only affected derivatives should be regenerated
- the update record should state that the semantic layer was unchanged

## Semantic Update Rules
When semantic meaning changes but artifact identity remains the same:

- apply the change to the structured markdown output first
- preserve untouched content
- preserve traceability unless explicit rebind is part of the request
- regenerate only affected derivatives
- record compatibility impact

## Required Update Recording
Every visual update should preserve or record:

- requested patch intent
- applied patch details
- preserved sections or untouched regions
- changed fields
- untouched fields
- whether renders were regenerated
- compatibility impact

This metadata may live in canonical update metadata, run metadata, or another
documented mechanism used consistently across the runtime.

## Rerender Rules
Visual rerenders must be generated from canonical state and applicable

Rules:

- rerender only the affected outputs when possible
- keep file names and derivative locations stable
- do not inject new semantic content
- do not erase semantic content that still exists canonically
- treat failure to regenerate faithfully as an integrity issue

## Ambiguity Rules
Stop and ask for clarification when any of the following is true:

- the target update scope is unclear
- the requested change would reorganize major visual structure
- source instructions conflict
- multiple layout interpretations would produce different canonical meaning
- the update would likely invalidate lineage, compatibility, or schema validity

## Family-Specific Reminder
These rules apply across boards, trees, matrices, flows, and rendered forms,
but each family should still preserve its own dominant structure:

- boards preserve grouping and section ownership
- trees preserve hierarchy and branch traceability
- matrices preserve row-column fidelity
- flows preserve direction and branch logic
- forms preserve section and field structure

## Phase-1 Intent
Phase 1 should favor safe, minimal, reviewable updates over ambitious
recomposition.

The priority order is:

1. canonical integrity
2. preserve unchanged content
3. deterministic rerendering
4. family-appropriate layout stability
5. clear update metadata
