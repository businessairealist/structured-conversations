# Render Contract

## Purpose
This file defines how structured outputs are rendered into human-consumable visual or presentation forms.

The goal is to produce consistent derivative outputs, support safe rerendering, and keep semantic content clearly separated from presentation and layout.

## Scope
This contract governs rendering behavior, renderer selection, render target handling, and render package expectations across collections and artifact families.

It applies to all plugin artifact families, including both visual and non-visual artifacts.

This file does not own the semantic schema in full, the project scaffold, folder layout, artifact placement rules, runtime orchestration, or naming rules in full. Those concerns are defined by the other shared references named below.

## Relationship to Other Shared References
`workspace-contract.md` defines runtime expectations, project-root behavior, and execution flow. This file assumes that runtime contract and defines only how derivatives must be produced from structured outputs.

`project-layout.md` defines the broader scaffold and directory model. This file does not redefine that scaffold.

`artifact-location-rules.md` defines where artifacts and outputs belong. This file only defines the derivative package structure and naming behavior inside an artifact when rendering is used.

`artifact-schema.md` defines structured output fields and semantic data structures. This file assumes that schema and does not redefine artifact semantics in depth.

`update-integrity-rules.md` defines update safety expectations. This file applies those expectations specifically to rendering and rerender behavior.

`artifact-lifecycle.md` defines versioning, supersession, compatibility, and stale-state behavior. This file does not redefine lifecycle policy.

`artifact-naming-conventions.md` defines naming and slug conventions. This file assumes those conventions and requires render outputs to remain consistent with them.

This file focuses on derivative presentation behavior: how structured outputs become HTML, Mermaid, SVG, preview images, `.feature` files, CSV exports, and other human-consumable render targets without changing semantic authority.

## Source-of-Truth and Derivative Principle
the structured markdown output is the semantic source of truth.

the human-readable summary, HTML, Mermaid, SVG, PNG, PDF, DOCX, CSV, `.feature`, and any other presentation or export outputs are derivatives unless another contract explicitly states otherwise.

Rendering must never become the hidden semantic source of truth.

A renderer must read semantic meaning from canonical content, not infer new authoritative meaning from a previously rendered file.

Manual edits to derivative outputs do not make those outputs canonical. If a semantic correction is needed, it must be applied to the structured markdown output first and then rendered again.

## Supported Renderer Families
The plugin supports the following renderer families:

- `board_renderer`: Renders board-like and canvas-like artifacts where cards, clusters, lanes, columns, or spatial groupings matter.
- `tree_renderer`: Renders hierarchical artifacts such as impact trees, opportunity-solution trees, hypothesis trees, or other parent-child structures.
- `matrix_renderer`: Renders grids, comparisons, rule/example/question tables, scoring matrices, and other row-column structures.
- `form_renderer`: Renders structured statement, template, or form-like presentations when a sectioned presentation view is needed.
- `flow_renderer`: Renders ordered sequences, process flows, delivery/task flows, and other directional or stepwise structures.

Renderer family selection must follow artifact family and semantic structure, not author preference alone.

A renderer may not switch an artifact into a different family just to satisfy a preferred visual style.

## Standard Render Package
The standard render package for visual artifacts is:


These files live inside the structured markdown output folder.

Not every visual artifact family must produce every derivative on every run, but when a derivative is present the package structure and naming must remain consistent.

The standard render package applies to visual artifact families. Non-visual artifact families may use family-specific derivative files instead of the visual package.

## Artifact Family Rendering Rules
### Board / canvas artifacts (`board_canvas_artifact`)
Typical renderer family: `board_renderer`.


HTML expectation: expected.

Mermaid expectation: optional only when the board can be represented faithfully as a simple graph, lane flow, or reduced structural diagram. Mermaid is usually inappropriate for dense boards, sticky-note style canvases, or artifacts whose meaning depends on rich spatial grouping.

Common derivatives: HTML, SVG, PNG preview, and optional export formats such as PDF when explicitly requested.

### Tree artifacts (`tree_artifact`)
Typical renderer family: `tree_renderer`.

Default render expectation: visual render package with HTML as the default render and Mermaid commonly available when the hierarchy can be represented faithfully.

HTML expectation: expected.

Mermaid expectation: often appropriate for clear hierarchical structures. Omit Mermaid if the artifact depends on layout richness, dense annotations, or interactions that Mermaid cannot preserve faithfully.

Common derivatives: HTML, Mermaid, SVG, PNG preview, and optional PDF when explicitly requested.

### Matrix artifacts (`matrix_artifact`)
Typical renderer family: `matrix_renderer`.

Default render expectation: visual render package with HTML as the primary review surface. Matrix artifacts often need precise row-column fidelity and benefit from stable HTML rendering.

HTML expectation: expected.

Mermaid expectation: optional but usually inappropriate for dense, tabular, scored, or comparison-heavy matrices. Use Mermaid only when the matrix can be reduced to a faithful simple diagram without losing meaning.

Common derivatives: HTML, SVG, PNG preview, and tabular exports such as CSV when the matrix is naturally exportable as rows and columns.

### Form / statement artifacts (`form_statement_artifact` and related markdown-first statement artifacts)
Typical renderer family: `form_renderer` when a structured presentation view is needed.

Default render expectation: canonical markdown-first package using the human-readable summary as the primary human-readable form. These artifacts are not visual by default.

HTML expectation: optional and request-driven, not required by default.

Mermaid expectation: usually inappropriate.

Common derivatives: the human-readable summary, optional HTML view, and optional DOCX or PDF exports when a formatted document is needed.

A form or statement artifact must not be forced into the visual render package unless the artifact family, request, or downstream workflow clearly requires a rendered presentation view.

### Scenario / executable specification artifacts (`scenario_executable_specification`)
Typical renderer family: no visual renderer is required by default. When a human-readable rendered documentation view is needed, `form_renderer` is the closest applicable family.

Default render expectation: canonical markdown plus scenario derivatives. The primary family-specific derivative is `scenarios.feature`. Optional human-readable documentation may be generated as HTML.

HTML expectation: optional, not required.

Mermaid expectation: usually inappropriate. A separate supporting flow diagram may exist, but it is not the canonical scenario derivative and should not replace `.feature` output.

Common derivatives: the human-readable summary, `scenarios.feature`, optional `docs.html`, and optional PDF or DOCX exports for stakeholder review.

### Plan / task-bundle artifacts (`plan_task_bundle_artifact`)
Typical renderer family: no visual renderer is required by default. `flow_renderer` may be used only when the plan is genuinely a stepwise or dependency-oriented flow.

Default render expectation: canonical markdown with family-specific exports such as `tasks.csv` and optional `plan.html`.

HTML expectation: optional, not required.

Mermaid expectation: usually inappropriate unless the artifact is explicitly a sequence, decision flow, or dependency flow.

Common derivatives: the human-readable summary, optional `plan.html`, `tasks.csv`, and optional PDF or DOCX exports when a delivery-ready document is needed.

## HTML Rendering Rules
HTML is the default visual render target for visual artifacts.

Use HTML when the artifact needs high fidelity, rich layout, dense labels, responsive presentation, or interaction patterns that Mermaid cannot represent faithfully.

HTML renderers must reflect canonical content and declared layout metadata without silently adding semantic meaning.

HTML may improve readability, navigation, filtering, or presentation, but it must not invent new nodes, relationships, statuses, or business logic.

HTML output should be stable enough for review and comparison across rerenders. Equivalent semantic content should produce materially equivalent structure, ordering, and labels unless a requested change or canonical update requires otherwise.

## Mermaid Rendering Rules
Mermaid is optional, not universal.

Mermaid is appropriate when the artifact can be represented faithfully as a graph, tree, flow, or other simple structured diagram.

Generate Mermaid only when it preserves the artifact’s meaning without material loss.

If fidelity would be poor, Mermaid must be omitted rather than approximated badly.

Mermaid is not required for artifacts whose meaning depends on rich layout, dense board semantics, matrix density, free placement, or presentation behavior that Mermaid does not support well.

When fidelity is in doubt, HTML remains the default render.

A Mermaid file is still a derivative. It must be generated from canonical content and must not become the maintained source of truth.

## Layout Separation Rules


If an artifact family uses placement or grouping that carries real semantic meaning, that meaning must also be represented explicitly in canonical semantic fields or in the documented artifact-family schema.

Semantic changes belong in the structured markdown output first.

Layout changes remain derivative unless the artifact family explicitly documents a layout element as semantically meaningful and that meaning is also represented canonically.

## Render Target Declaration Rules
`render_targets` in the structured markdown output conceptually declare intended or supported derivative outputs.

Render target declaration is semantic metadata about supported derivatives. It tells renderers and downstream tools what outputs are allowed or expected.

Generated files are implementation outputs. A declared render target does not guarantee that the file has already been generated.

A declared render target does not make the generated file canonical.

Render targets should be declared conservatively. A target should be declared only when the artifact family supports it and the target can be produced faithfully.

For visual artifacts, HTML should normally be the default declared visual target. Mermaid should be declared only when faithful representation is realistic for that artifact.

## Render Generation Rules

Rendered files are not primary editable sources.


Renderer scripts are the operational mechanism that create outputs. This file defines the contract those scripts must follow.

Renderer selection must stay consistent with artifact family, declared render targets, and fidelity requirements.

If presentation polishing would require semantic interpretation, the structured markdown output must be updated first. The renderer may not hide semantic edits inside HTML, Mermaid, SVG, CSV, or any other derivative.

## Partial Update and Rerender Rules
Partial updates apply to the structured markdown output first.

After a valid semantic update, only affected derivatives should be regenerated as needed.

The plugin must preserve unchanged nodes, cards, metadata, and stable identifiers whenever possible.

The update record must state whether renders were regenerated.

Requested patch metadata should remain explicit. At minimum, update processing should preserve or record:

- requested patch intent
- applied patch details
- preserved sections or untouched regions
- whether rerendering occurred

Rerendering must not cause unrelated content drift.

A requested change to one card, branch, row, statement, scenario, or task must not silently rewrite unrelated labels, reorder unrelated structures, or alter unaffected presentation sections unless the change logically requires it.

## Stability and Integrity Expectations
When semantic identity is unchanged, rerendering should preserve the following:

- artifact identifier
- stable node or item IDs when applicable
- preserved unchanged sections
- provenance and traceability links
- deterministic file names and derivative locations

Rerendering must not invent semantic content.

Rerendering must not erase semantic content that still exists canonically.

Presentation differences should follow actual semantic changes or explicitly requested layout changes, not incidental renderer noise.

Stable semantic inputs should lead to stable derivative outputs that are easy to diff, review, and trust.

## Render Example Library Usage Rules
Rendered examples and visual markdown guides may guide layout patterns, labeling conventions, density choices, and rendering style.

Examples may influence presentation style, but they must not override structured output content.

Examples are advisory references, not substitute schemas.

When an example reference is used, the chosen example reference should be recorded in execution notes.

Example usage must not create hidden coupling between the current artifact and unrelated example semantics.

A renderer may borrow presentation conventions from an example library, but it may not import example nodes, labels, rules, or business meaning unless those elements are present in canonical content.

## Failure and Clarification Rules
A renderer should stop and request clarification when any of the following is true:

- the artifact family and requested render target do not match
- Mermaid is requested but faithful Mermaid representation would be poor
- semantic content required for rendering is missing
- a requested structural update would materially alter layout or meaning and is ambiguous
- layout metadata is inconsistent with canonical content in a way that cannot be safely resolved

A renderer may proceed automatically when the artifact family is clear, the requested target is supported, required canonical content is present, fidelity is acceptable, and layout metadata is valid or safely regenerable without semantic ambiguity.

A renderer must omit a derivative target rather than generate a misleading one.

Failing closed is better than producing a plausible-looking but semantically wrong render.

## Non-Negotiable Rules
- the structured markdown output is the source of truth.
- HTML is the default visual render target.
- The default open target for users should be the most human-friendly review surface, not raw canonical JSON.
- Mermaid is allowed only when it is faithful.
- Render package naming must remain consistent when present.
- Semantic updates happen in canonical content first.
- Rerendering must not cause semantic drift.
- Derivatives are review surfaces and exports, not hidden semantic authorities.

## Quick Compliance Checklist
- Is the structured markdown output still the semantic source of truth?
- Does the selected renderer family match the artifact family and structure?
- Is HTML used as the default visual render where the artifact is visual?
- Is Mermaid generated only when it is faithful?
- Are derivative file names and locations consistent with the contract?
- Were semantic updates applied before rendering?
- Were unchanged sections and stable identifiers preserved where possible?
- Was rerendering limited to affected derivatives?
- Was render regeneration recorded?
- Were example references treated as presentation guidance only?
- Was any misleading derivative omitted instead of generated?
