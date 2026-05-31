# Artifact Schema

## Purpose
This file defines the canonical schema contract for generated artifacts.

Its goal is to make artifacts consistent, discoverable, safely reusable, compatible across dependent skills, and reliable for chaining across the full workspace system.

This contract exists so skill authors, validators, renderers, and artifact transformers can rely on the same base meaning for the same canonical fields.

## Scope
This file governs the semantic structure of structured outputs and the schema behavior that every structured output package must satisfy.

It applies across all collections and all artifact families, including text artifacts, visual artifacts, executable specification artifacts, and other family-specific canonical packages.

This file does not own project scaffold layout, artifact placement, naming, or runtime orchestration. Those concerns are defined in sibling shared references.

## Relationship to Other Shared References
This file defines what structured artifact data must exist and what that data means.

It complements, but does not replace, the other shared references:

- `workspace-contract.md` defines how skills resolve the workspace root, search for inputs, and write outputs.
- `project-layout.md` defines the project scaffold and directory layout.
- `artifact-location-rules.md` defines where artifacts are stored.
- `artifact-naming-conventions.md` defines naming and slug rules.
- `render-contract.md` defines rendering behavior and render package details.
- `artifact-lifecycle.md` defines lifecycle handling beyond the base schema surface.
- `update-integrity-rules.md` defines update-safety expectations and mutation controls.
- `evidence-normalization.md` defines how evidence is normalized before being linked into artifacts.

This file focuses on canonical schema meaning, field responsibility, compatibility-visible metadata, and update-safe semantic structure.

## structured output Package
Every structured output is a folder-based package.

The package is the unit of reuse, traceability, and update.

A structured output package normally contains:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

Additional derivative files may exist, including render outputs, previews, layout files, or family-specific helper files. Those derivatives do not replace the canonical files listed above.

## Source-of-Truth Principle
the structured markdown output is the semantic source of truth for the artifact.

the human-readable summary is a human-readable derivative of the canonical semantic payload. Rendered outputs are also derivatives.

No downstream skill may treat HTML, Mermaid, SVG, PNG, PDF, DOCX, CSV, or any other export as the canonical semantic source unless another explicit contract says so for a specific artifact family.

When canonical data and a derivative disagree, downstream systems must trust the structured markdown output and treat the derivative as stale or invalid until regenerated.

## Required Canonical Files
### the structured markdown output
Owns the canonical semantic payload and the minimum machine-usable metadata required for chaining, compatibility checks, render selection, and update handling.

### the human-readable summary
Owns the primary human-readable narrative view of the artifact. It should explain or summarize the structured markdown output in a way people can review quickly, but it does not replace the semantic source of truth.

### execution notes
Owns run metadata and execution context. This includes generation context, selected references or examples when relevant, input/output file paths, changed fields when relevant, and other per-run details that should not redefine the canonical semantic payload.

### source traceability notes
Owns rich lineage and dependency detail. It records where the artifact came from, what upstream artifacts or evidence it depends on, and what transformations or derivations connect those sources to the current artifact.

### open questions
Owns unresolved issues, pending decisions, follow-up items, and unanswered questions that remain open after artifact generation or update.

In plain terms:

- semantic content belongs in the structured markdown output
- human-readable narrative belongs in the human-readable summary
- run metadata belongs in execution notes
- lineage detail belongs in source traceability notes
- unresolved issues belong in open questions

## Base Artifact Schema
the structured markdown output is the base canonical schema shared across all artifact families.

Every artifact family must satisfy the base schema even when it adds family-specific fields or family-specific content structures.

Family-specific extensions must be additive and non-breaking unless the artifact versioning and compatibility metadata are updated in a way that makes the break explicit.

A family may specialize the shape of `content`, add family-specific validation rules, or add family-specific metadata. It may not bypass the base contract or remove required base meaning from required fields.

## Required Fields in the structured markdown output
### Mandatory base fields
The following fields are mandatory in every canonical the structured markdown output:

- artifact identifier
- artifact type
- artifact version
- `collection`
- `created_by_skill`
- `created_at`
- `updated_at`
- `status`
- `source_artifacts`
- `inputs`
- `content`
- `assumptions`
- `open_questions`
- `traceability`
- `render_targets`

### Strongly expected lifecycle and compatibility fields
The following fields are strongly expected as part of the base schema support surface. They may be omitted only when genuinely not applicable:

- `supersedes_artifact identifier`
- `compatible_with`
- `stale_reason`
- `recompute_required_for`
- `partial_update_supported`
- `user_experience`

These fields are not optional from a system design perspective. A skill or validator should expect the schema to support them, even if the value in a particular artifact is `null`, empty, or otherwise marked as not applicable.

## Field Definitions
### artifact identifier
- Represents: the stable, unique identifier for the structured markdown output.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: must remain stable across rerenders and partial updates when the artifact is still the same structured output.
- Common pitfalls: changing the ID for rerenders, using file names as IDs, or reusing an ID across distinct artifacts.

### artifact type
- Represents: the semantic kind of artifact.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: should remain stable unless the artifact changes to a different semantic kind.
- Common pitfalls: using file format names such as `json`, `pdf`, or `html` instead of semantic kinds such as a board, tree, matrix, document artifact, executable spec, plan bundle, or similar artifact kind.

### artifact version
- Represents: the current version of the structured markdown output as a semantic object, including version-significant content or interpretation changes.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: must change when semantic content changes materially or when downstream interpretation would change in a meaningful way.
- Common pitfalls: using render timestamps as artifact versions, failing to increment on meaningful semantic changes, or using it only for file revisions while ignoring compatibility impact.

### `collection`
- Represents: the owning collection for the artifact.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: should align to the collection IDs used by the project inventory.
- Common pitfalls: using display labels instead of inventory IDs, or moving artifacts across collections without explicit lifecycle handling.

Valid collection IDs include:

- `foundation-routing`
- `mapping-discovery`
- `vision-messaging`
- `feature-specification`
- `story-delivery`
- `quality-diagnostics`
- `strategy-experimentation`

### `created_by_skill`
- Represents: the skill identifier responsible for creating the artifact.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: should not change after initial creation.
- Common pitfalls: overwriting the creator on update instead of recording update activity elsewhere.

### `created_at`
- Represents: the timestamp when the artifact was first created.
- Requirement level: required.
- Audience: machine-facing.
- Stability expectation: immutable after creation.
- Common pitfalls: resetting it during updates or rerenders.

### `updated_at`
- Represents: the timestamp of the most recent canonical semantic update.
- Requirement level: required.
- Audience: machine-facing.
- Stability expectation: must update when semantic content changes; may remain unchanged for pure file-copy operations that do not change the structured markdown output.
- Common pitfalls: updating it for non-semantic render-only actions, or failing to update it after semantic edits.

### `status`
- Represents: the current lifecycle state of the artifact.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: should change only when lifecycle state changes.
- Common pitfalls: using vague free-text labels with no operational meaning, or treating status as a cosmetic field.

The value should make the current lifecycle state detectable, such as draft, active, superseded, stale, deprecated, blocked, or another implementation-approved lifecycle state.

### `source_artifacts`
- Represents: direct references to upstream structured outputs or source evidence used to produce this artifact.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: unchanged upstream dependencies should remain preserved across partial updates.
- Common pitfalls: storing only human prose with no resolvable references, or dropping upstream links during transformations.

### `inputs`
- Represents: the resolved inputs used for this artifact, including user instructions, evidence bundles, selected upstream artifacts, or normalized source references.
- Requirement level: required.
- Audience: both.
- Stability expectation: should reflect the actual resolved inputs for the current structured output version.
- Common pitfalls: confusing inputs with provenance, or storing only vague summaries that downstream skills cannot reason over.

### `content`
- Represents: the main semantic payload of the artifact.
- Requirement level: required.
- Audience: both.
- Stability expectation: unchanged semantic sections should be preserved across partial updates.
- Common pitfalls: storing presentation-only layout details here, reducing content to unstructured prose when structure is needed, or making content impossible for validators and transformers to inspect.

### `assumptions`
- Represents: non-proven premises that the artifact currently depends on.
- Requirement level: required.
- Audience: both.
- Stability expectation: should remain explicit until confirmed, removed, or replaced.
- Common pitfalls: hiding assumptions inside narrative prose, mixing assumptions with questions, or omitting assumptions because they feel obvious.

### `open_questions`
- Represents: unresolved questions that affect confidence, completeness, or next-step handling.
- Requirement level: required.
- Audience: both.
- Stability expectation: should persist until resolved, explicitly closed, or moved to resolved history outside the base field.
- Common pitfalls: using open questions as a dumping ground for assumptions, or leaving the field absent when the artifact clearly has unresolved issues.

### `traceability`
- Represents: machine-usable linkage that explains lineage, semantic anchors, dependency relationships, or downstream reasoning hooks.
- Requirement level: required.
- Audience: both.
- Stability expectation: lineage that still applies should remain stable across rerenders and partial updates.
- Common pitfalls: making traceability purely narrative, failing to preserve stable references, or making downstream dependency reasoning impossible.

### `render_targets`
- Represents: the declared derivative render forms that the artifact supports or intends to support.
- Requirement level: required.
- Audience: machine-facing and human-facing.
- Stability expectation: should change when render support changes.
- Common pitfalls: treating render outputs as canonical content, declaring unsupported render targets, or requiring Mermaid when fidelity would be poor.

### `supersedes_artifact identifier`
- Represents: the prior artifact that this artifact supersedes.
- Requirement level: conditionally required when a new structured output replaces an older one.
- Audience: machine-facing and human-facing.
- Stability expectation: immutable once set.
- Common pitfalls: using it for minor rerenders of the same artifact, or omitting it when a true replacement has occurred.

### `compatible_with`
- Represents: compatibility declarations used by downstream skills to decide whether the artifact is safe to consume.
- Requirement level: strongly expected; conditionally required when compatibility is relevant to chaining.
- Audience: machine-facing.
- Stability expectation: must reflect the current artifact version and intended compatibility surface.
- Common pitfalls: using informal prose only, or assuming newest automatically means compatible.

### `stale_reason`
- Represents: why the artifact should be treated as stale or no longer safely chainable without refresh.
- Requirement level: conditionally required when status or dependency state indicates staleness.
- Audience: both.
- Stability expectation: should remain until staleness is cleared by recomputation or lifecycle transition.
- Common pitfalls: marking artifacts stale without explaining why, or leaving stale artifacts undetectable.

### `recompute_required_for`
- Represents: what downstream uses, consumers, or dependency conditions require recomputation before safe use.
- Requirement level: conditionally required when upstream changes invalidate current compatibility.
- Audience: both.
- Stability expectation: should reflect the current invalidation scope.
- Common pitfalls: using vague text like "some downstream uses," or omitting the field when compatibility is broken.

### `partial_update_supported`
- Represents: whether the artifact family and current artifact support controlled partial updates without full regeneration.
- Requirement level: strongly expected.
- Audience: machine-facing.
- Stability expectation: should stay stable for the artifact family unless explicit lifecycle or schema change says otherwise.
- Common pitfalls: marking everything as partial-update-safe, or failing to account for structural cases that require full recomputation or clarification.

### `user_experience`
- Represents: human-facing metadata used by the artifact library and natural conversation-based retrieval.
- Requirement level: strongly expected.
- Audience: human-facing first, machine-usable second.
- Stability expectation: should update when user-visible title, summary, review focus, or next-step guidance changes materially.
- Common pitfalls: forcing users to navigate by slug or path because no human title, topic, or review surface is exposed.

## Recommended Schema Organization
the structured markdown output should be organized consistently so humans and scripts can find the same kinds of information in the same places.

A recommended organization is:

- identity fields
- lifecycle fields
- input and provenance linkage fields
- semantic content fields
- assumptions and open-questions fields
- render declarations
- compatibility and update fields

One acceptable layout is:

```json
{
  "artifact identifier": "...",
  "artifact type": "...",
  "artifact version": "...",
  "collection": "...",
  "created_by_skill": "...",
  "created_at": "...",
  "updated_at": "...",
  "status": "...",

  "source_artifacts": [],
  "inputs": {},
  "traceability": {},

  "content": {},

  "assumptions": [],
  "open_questions": [],

  "render_targets": [],

  "supersedes_artifact identifier": null,
  "compatible_with": {},
  "stale_reason": null,
  "recompute_required_for": [],
  "partial_update_supported": true
}
```

This organization is recommended for consistency. It is not a requirement to use this exact nesting shape if a flatter or slightly different arrangement better matches the artifact family and still preserves the base field contract.

## Content Modeling Rules
`content` is the main semantic payload of the artifact.

Its structure may vary by artifact family, but it must remain structured, machine-usable, and semantically meaningful.

`content` must model what the artifact means. It must not be reduced to presentation layout or export-only formatting.

Human-readable prose summaries belong in the human-readable summary unless that prose is itself part of the artifact’s meaning.

Visual positioning, rendering coordinates, canvas placement, and other layout-only details should live in layout-related derivatives such as render packages or layout files, not inside `content`, unless position or ordering is itself semantically meaningful.

A content model should make downstream transformation possible. If another skill needs to translate a board into a tree, or a story into executable scenarios, the content model should expose the semantic units needed for that transformation.

## Render Target Modeling Rules
`render_targets` declares supported derivative render forms.

The declaration must be structured and machine-readable. It may be represented as a keyed object, a list of target descriptors, or another unambiguous structure approved by the artifact family, but it must clearly state what render targets are supported or intended.

For visual artifacts:

- HTML is the default visual render target.
- Mermaid is optional and should only be declared when the artifact can be represented faithfully.
- Absence of Mermaid is valid when Mermaid fidelity would be poor.

`render_targets` declares support and intent. `render-contract.md` defines rendering behavior, renderer families, render package structure, and derivative file conventions in detail.

Render declarations must not be used to redefine the artifact’s canonical semantics.

## Provenance and Traceability Modeling Rules
`source_artifacts` in the structured markdown output records the direct upstream artifacts or source evidence that this artifact depends on.

source traceability notes holds richer lineage detail, including transformation relationships, dependency detail, evidence normalization references, and other history that is too detailed for the base field surface.

`traceability` in the structured markdown output should provide the compact, machine-usable links that downstream skills need for reasoning, validation, and chaining.

Transformed artifacts must preserve upstream lineage. A downstream artifact must not sever the chain back to the upstream structured output or normalized evidence that informed it.

A downstream skill should be able to answer three questions from canonical metadata:

- Where did this artifact come from?
- What does it depend on?
- What would likely need recomputation if an upstream dependency changes?

## Lifecycle and Compatibility Modeling Rules
The schema must support visible handling for:

- supersession
- compatibility
- staleness
- recomputation triggers
- partial update support

`supersedes_artifact identifier` is used when a new artifact replaces an older one.

`compatible_with` must make downstream compatibility reasoning possible. Compatibility may be expressed against artifact types, versions, schemas, workflows, quality gates, or other approved compatibility anchors.

`stale_reason` must make staleness detectable. If upstream change breaks safe reuse, the artifact must not appear healthy by omission.

`recompute_required_for` must identify the downstream uses or dependency paths that now require refresh.

`partial_update_supported` must make it possible for scripts and skills to determine whether a controlled partial edit is allowed.

Latest-compatible resolution depends on these fields. Newest and compatible are not the same. A newer artifact may still be unusable for a downstream skill if compatibility has been broken or staleness has been declared.

Incompatible or stale artifacts must be detectable from canonical metadata without reading rendered derivatives.

## Assumptions and Open Questions Modeling Rules
Assumptions and open questions are related but not interchangeable.

Assumptions are non-proven premises the artifact currently relies on. They say, in effect, "this artifact currently depends on this being true."

Open questions are unresolved issues that still need an answer. They say, in effect, "this decision or fact is still unknown."

Both must appear in the structured markdown output in compact form so downstream skills can quickly understand risk and incompleteness.

Detailed unresolved issue records should live in open questions when more structure is needed, such as owner, priority, blocking status, or follow-up action.

Assumptions should be explicit enough that downstream users can understand the risk surface without reading external notes.

A common rule:

- if the artifact currently proceeds on a premise, record an assumption
- if the artifact cannot yet resolve something, record an open question

## Partial Update Modeling Rules
Partial updates apply to the structured markdown output first.

A partial update must update canonical semantics before any derivative is regenerated.

The schema must support recording:

- `requested_patch`
- `applied_patch`
- `preserved_sections`
- render regeneration status

This recording may live directly in canonical metadata when the artifact family includes it there, or in linked update metadata such as execution notes, as long as the update remains machine-auditable.

Unchanged semantic sections, stable IDs, and applicable lineage must be preserved whenever possible.

When a requested change would require ambiguous structural mutation, incompatible schema mutation, or unsupported partial editing, the correct behavior is clarification or explicit replacement handling, not speculative mutation.

## Artifact Family Extension Rules
Artifact families may extend the base schema for boards, trees, matrices, forms, executable specs, plan bundles, document artifacts, and other canonical families.

Family-specific fields must not break the base contract.

Family-specific extensions should add structured semantic content, family-specific metadata, or family-specific validation rules. They must not bypass required base fields.

A family may specialize:

- the structure of `content`
- the structure of `traceability`
- family-specific compatibility rules
- family-specific render target declarations
- family-specific helper metadata needed for safe transformation

A family should not move semantic meaning into render-only derivatives when that meaning is needed for chaining, validation, or downstream transformation.

When possible, keep layout and render derivatives separate from semantic content.

## File Responsibility Boundaries
### What belongs in the structured markdown output
- canonical semantic payload
- required base fields
- compact traceability and dependency linkage
- assumptions and open-questions summaries
- lifecycle and compatibility-visible metadata
- user-facing discovery metadata
- render target declarations

### What belongs in the human-readable summary
- human-readable narrative summary
- reviewer-friendly explanation of the artifact
- structured prose views derived from canonical content

### What belongs in execution notes
- run metadata
- execution context
- selected references or examples
- input and output file paths
- changed fields when relevant
- patch application detail when relevant
- render regeneration detail when relevant

### What belongs in source traceability notes
- lineage detail
- upstream dependency detail
- transformation history
- evidence normalization references
- richer dependency chains than the compact base fields should hold

### What belongs in open questions
- unresolved questions
- blocking issues
- follow-up items
- owners, priorities, or statuses for unresolved decisions when needed

The boundary rule is simple: the structured markdown output should stay canonical and operationally essential; other files should expand or explain, not redefine.

## Stability and Compatibility Expectations
The following should remain stable across rerenders and partial updates whenever the artifact is still the same structured output:

- artifact identifier
- the artifact’s stable semantic identity
- applicable lineage and traceability anchors
- unchanged content sections

Create an updated artifact in place when the artifact is still the same semantic object and only the requested parts are changing under supported lifecycle rules.

Create a new artifact when the semantic identity changes materially, the artifact changes kind, the lifecycle requires explicit replacement, or downstream interpretation would break without a new supersession boundary.

When a new artifact replaces an older one, record that relationship explicitly with `supersedes_artifact identifier` and related lifecycle metadata.

Schema changes that break downstream interpretation require explicit versioning and compatibility handling. They must not be introduced silently.

## Schema Validation Expectations
All structured outputs should validate against the base schema before they are registered as successful outputs.

Validation should happen before downstream chaining.

Invalid artifacts must not be treated as reliable canonical sources, even if a human-readable derivative looks correct.


## Non-Negotiable Rules
- the structured markdown output is the semantic source of truth.
- Every structured output package must contain the required canonical files.
- Every the structured markdown output must contain all mandatory base fields.
- structured outputs must preserve traceability to upstream artifacts or source evidence.
- structured outputs must expose lifecycle and compatibility-visible metadata.
- Visual artifact support must treat HTML as the default visual render target and Mermaid as optional when faithful.
- Partial updates must update canonical semantics first and preserve unchanged sections, stable IDs, and lineage whenever possible.
- Invalid structured outputs must not be treated as safe inputs for downstream chaining.

## Quick Compliance Checklist
- [ ] The artifact is packaged as a folder-based structured output package.
- [ ] The package contains the structured markdown output, the human-readable summary, execution notes, source traceability notes, and open questions.
- [ ] the structured markdown output is present and treated as the semantic source of truth.
- [ ] All mandatory base fields are present in the structured markdown output.
- [ ] Lifecycle and compatibility support fields are present or explicitly marked not applicable.
- [ ] `content` is structured, machine-usable, and semantic rather than presentation-only.
- [ ] `source_artifacts`, `inputs`, and `traceability` make upstream dependency reasoning possible.
- [ ] `assumptions` and `open_questions` are explicit and understandable.
- [ ] `render_targets` accurately declares supported derivative render modes.
- [ ] Partial update behavior, if supported, preserves stable IDs, lineage, and unchanged sections.
- [ ] The artifact validates against the base schema before registration and downstream reuse.
