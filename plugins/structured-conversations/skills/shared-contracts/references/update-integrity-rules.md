# Update Integrity Rules

## Purpose
This file defines how structured outputs may be changed without corrupting meaning, lineage, compatibility, or render trustworthiness.

The goal is safe change, reliable diffs, trustworthy reuse, and low-drift downstream chaining across independently callable skills, shared scripts, and artifact transformers.

These rules exist to prevent silent semantic drift, hidden identity changes, broken downstream assumptions, and misleading rendered outputs.

## Scope
This file governs integrity-preserving update behavior for structured outputs and their derivatives.

It applies across collections, artifact families, and runtime profiles wherever a skill or script updates an existing output package or regenerates derivative outputs.

This file does not restate full placement, schema, naming, lifecycle, or rendering details. Those are handled more fully in sibling shared references and are only referenced here where they affect update safety.

## Relationship to Other Shared References
`workspace-contract.md` defines how skills resolve project context, locate artifacts, and operate inside the workspace. This file assumes the target artifact has already been selected.

`artifact-schema.md` defines canonical structure and field expectations. This file governs how updates may be applied without violating that structure.

`artifact-location-rules.md` defines where artifacts and derivatives live. This file governs how updates preserve those locations when identity remains stable.

`artifact-lifecycle.md` defines versioning, stale handling, compatibility, and supersession. This file governs when an update remains in place versus when it becomes a superseding change.

`render-contract.md` defines renderer families, render packages, and derivative expectations. This file governs safe regeneration behavior after canonical updates.

`artifact-naming-conventions.md` defines naming and path consistency. This file governs when those names stay stable and when a new artifact identity is required.

This file focuses on how changes are applied safely once the correct target artifact has been identified.

## Core Integrity Principles
The following are hard contract rules:

- the structured markdown output is updated first for any canonical semantic change.
- Only requested fields, sections, nodes, cards, or metadata may be changed.
- Unchanged nodes, cards, sections, and metadata must be preserved.
- Upstream traceability must be preserved unless an explicit and safe rebind is part of the requested change.
- Stable identifiers must be preserved whenever possible.
- Rerendering must not create unrelated semantic drift.
- Ambiguity that risks schema validity, compatibility, structure, or lineage requires clarification before any update is applied.
- Rendered outputs are derivatives of canonical state and are not the primary source of truth.
- Stable identity may be preserved only when the artifact remains meaningfully the same artifact.

## Update Classes
### Metadata-only update
A metadata-only update changes non-semantic fields such as status, timestamps, compatibility markers, or other administrative fields without changing the core meaning of the artifact.

Safeguards:
- Do not alter semantic content.
- Record the changed fields.
- Preserve stable identity, lineage, and render package structure.
- Regenerate derivatives only if the metadata is rendered or exposed downstream.

### Content partial update
A content partial update changes a clearly targeted portion of canonical content while leaving the rest of the artifact intact.

Safeguards:
- The target section must be explicit.
- Unchanged content must remain semantically and structurally stable.
- Schema validity must be preserved.
- Compatibility impact must be assessed and recorded.

### Layout-only derivative update
A layout-only derivative update changes presentation or render arrangement without changing canonical meaning.

Safeguards:
- Do not silently alter semantic content in the structured markdown output.
- Preserve stable node or card IDs where layout references them.
- Regenerate only the affected derivatives.
- Record that the semantic layer was unchanged.

### Semantic update preserving identity
A semantic update preserving identity changes artifact meaning in a bounded way while the artifact still represents the same underlying work item, model, map, document, or decision object.

Safeguards:
- Apply the change canonically in the structured markdown output first.
- Preserve stable identity and lineage continuity.
- Record patch metadata and compatibility impact.
- Regenerate affected derivatives from canonical state.

### Structural change requiring clarification
A structural change requiring clarification is any requested update that would reorganize major semantic sections, rewrite large portions of the artifact, or change the artifact’s internal model without sufficient clarity.

Safeguards:
- Do not guess.
- Stop and request clarification.
- Do not perform a partial structural rewrite under the label of a safe in-place update.

### Superseding replacement
A superseding replacement is required when the requested change produces a materially new artifact or when preserving the old identity would mislead downstream users or scripts.

Safeguards:
- Create a new or superseding artifact instead of hiding the change inside the old one.
- Preserve lineage through explicit supersession metadata.
- Keep historical continuity auditable.

## Artifact-JSON-First Rule
Canonical semantic changes must be applied to the structured markdown output first.

Derivative files such as the human-readable summary, HTML, Mermaid, SVG, PNG, DOCX, PDF, CSV, preview images, and other exports must be regenerated or reconciled from canonical state rather than edited as the primary authority.

Direct derivative-only editing is not a valid substitute for canonical update. A skill or script must not treat a rendered file as the authoritative source when the requested change affects artifact meaning, structure, traceability, compatibility, or any canonical field.

If a derivative file was edited manually outside the canonical process, that file must be reconciled back into canonical state before it can be trusted as current.

## Preserve-Unchanged-Content Rule
Preserving unchanged content means keeping all non-targeted semantic content, metadata, lineage, and stable identifiers intact when they are not part of the requested change.

A valid update must not rewrite unrelated sections only because the artifact was reopened, rerendered, normalized, or passed through a different script version.

Preserving unchanged content applies to:
- semantic sections not targeted by the request
- metadata not targeted for change
- provenance and traceability information
- stable node, card, row, column, or section identifiers where applicable
- derivative file names and locations when artifact identity remains the same

This rule exists to preserve trustworthy diffs, stable downstream references, and confidence that an update changed only what it claimed to change.

## Stable Identity and Stable Section Rules
When an artifact remains the same artifact, the following should remain stable:

- artifact identifier
- stable node, card, section, or element IDs where relevant
- unchanged semantic sections
- provenance continuity
- expected canonical file names
- expected derivative locations for the same output package

The following may legitimately change during a valid update:

- `updated_at`
- targeted content fields
- status when appropriate
- compatibility markers
- render outputs regenerated after the valid canonical update
- layout metadata when the request is presentation-only and semantic meaning is preserved

Stable identity is not a license to hide a fundamentally new artifact inside an old one. If the artifact’s purpose, interpretation, or semantic scope changes materially, the update must become a superseding artifact rather than an in-place mutation.

## Patch Recording Rules
Every update must be auditable after the fact.

Update tracking must explicitly record at least the following fields or equivalent documented representations:

- `requested_patch`
- `applied_patch`
- `preserved_sections`
- `render_regenerated`
- `changed_fields`
- `untouched_fields`
- `compatibility_impact`

This metadata may live in manifest update metadata, canonical update metadata, or another documented mechanism consistent with the shared schema, provided later skills and scripts can inspect it reliably.

`requested_patch` records what the caller asked to change.

`applied_patch` records what was actually changed.

`preserved_sections` records which sections or structures were intentionally left unchanged.

`render_regenerated` records whether derivative outputs were regenerated and, when useful, which ones.

`changed_fields` records the canonical fields or structures that changed.

`untouched_fields` records the areas intentionally left intact.

`compatibility_impact` records downstream implications in terms later skills can interpret.

## Compatibility Impact Rules
Every meaningful update must assess whether compatibility with downstream consumers has changed.

Compatibility impact may be one of the following:

- none
- limited but safe
- requires downstream recomputation
- incompatible enough to require supersession or clarification

A skill or script must evaluate whether downstream artifacts, transforms, quality gates, renderers, or selectors depend on the changed fields, structures, or semantics.

If the update changes assumptions that downstream consumers rely on, the update must record the impact clearly and mark recomputation or stale relationships where appropriate.

Compatibility-related fields and downstream implications must remain understandable to later skills. Do not encode compatibility effects in ambiguous prose that cannot be interpreted reliably.

## Render Regeneration Rules
Derivative renders must be regenerated only as needed after a valid canonical update.

Rerendering must happen from canonical state plus any applicable layout metadata, not from prior rendered files.

Rerendering must not introduce unrelated content drift. A renderer may update presentation, formatting, coordinates, or deterministic layout output, but it must not silently rewrite canonical meaning.

Deterministic file names and derivative locations should remain stable when artifact identity remains stable.

If a derivative cannot be faithfully regenerated from current canonical state, the system must treat that as an integrity issue rather than silently emitting a misleading render.

## Visual Update Integrity Rules
Visual artifact updates must preserve unchanged nodes, cards, sections, and metadata, along with stable node or card IDs whenever possible.

Layout adjustments must not silently rewrite semantic meaning. A move, regrouping, or relabeling operation that changes interpretation is a semantic update and must be handled as such in canonical state.

HTML is the default visual render. Mermaid is optional only when the artifact can be represented faithfully.

A visual update request that would materially alter board, tree, matrix, form, or flow structure without sufficient clarity must stop and request clarification.

Examples and reference layouts may guide presentation, spacing, and labeling style, but they must not override canonical content during update.

Visual derivatives must be regenerated from canonical state after a valid canonical update. Editing HTML, Mermaid, SVG, or preview images directly is not a valid substitute for updating the structured markdown output.

## Safe Partial Update Rules
A safe in-place partial update is allowed only when all of the following are true:

- artifact identity remains the same
- the requested target is clear
- partial update is supported, or at minimum not contradicted by the artifact contract
- schema validity can be preserved
- lineage can be preserved without deception
- compatibility impact is understood and acceptable
- the change does not hide a major semantic replacement inside an existing artifact identity

Safe partial updates are preferred when they preserve continuity, minimize unnecessary churn, and keep downstream references stable.

A partial update is not safe merely because the changed text is small. The deciding factor is whether the change is local, explicit, schema-safe, and honest about compatibility and identity.

## Ambiguous or Structural Change Rules
A requested update is too ambiguous or too structural to apply automatically when any of the following is true:

- the target section is unclear
- the update scope is unclear
- source instructions conflict
- the request would reorganize large semantic structures without clear intent
- the request could invalidate schema, compatibility, or lineage
- the request could require hidden assumptions about structure or meaning
- multiple reasonable interpretations would lead to different canonical outcomes

In these cases, the skill or script must stop and ask rather than guessing.

Large rewrites, structure changes, semantic reframing, or artifact-family shifts must not be smuggled through a partial update path just because the caller requested an “update.”

## When to Create a Superseding Artifact Instead
Create a new or superseding artifact instead of applying an in-place update when any of the following is true:

- semantic identity changes materially
- scope or purpose changes substantially
- downstream interpretation would change in a non-local way
- preserving stable identity would be misleading
- the artifact changes into a different deliverable, framing, or contract surface
- the requested change would erase meaningful historical interpretation
- compatibility impact is large enough that downstream consumers should not treat the result as the same artifact

Supersession must preserve lineage rather than erasing history. The new artifact should declare its relationship to the prior artifact using the lifecycle and compatibility mechanisms defined in the shared schema and lifecycle references.

## Downstream Traceability Preservation Rules
Updates must preserve `source_artifacts`, provenance continuity, and any downstream-relevant traceability unless the change explicitly and safely rebinds them.

An updated artifact must still explain where it came from, what changed, and why the updated form remains trustworthy.

Traceability links must remain usable by later skills, scripts, and artifact consumers. Do not remove or overwrite source relationships merely because the artifact has been refreshed, rerendered, or partially rewritten.

If traceability is intentionally rebound, that change must be explicit, schema-valid, and recorded as part of the applied update metadata.

## Failure and Clarification Rules
A skill or script must stop and ask for clarification when any of the following is true:

- there are multiple plausible target artifacts
- the target section is ambiguous
- it is unclear whether to update in place or create a superseding artifact
- compatibility impact is uncertain
- schema validity is at risk
- lineage continuity is at risk
- the request requires hidden structural assumptions
- a visual structure change would materially alter meaning without clear instruction

A skill or script may proceed automatically when the target is unambiguous, the scope is explicit, schema validity can be preserved, lineage remains trustworthy, and compatibility impact is known or acceptably minimal.

A skill or script must refuse to guess when guessing would risk semantic corruption, traceability loss, broken compatibility, or misleading outputs.

When stopping for clarification, the unresolved issue should be described in concrete terms: what is unclear, what cannot be safely inferred, and whether the likely resolution is an in-place update, a structural rewrite, or a superseding artifact.

## Non-Negotiable Rules
- Update the structured markdown output first for canonical semantic changes.
- Change only the requested fields or sections.
- Preserve unchanged content.
- Preserve stable IDs where possible.
- Preserve lineage and downstream traceability.
- Record patch metadata for every update.
- Assess and record compatibility impact.
- Regenerate derivatives safely from canonical state.
- Keep derivative names and locations stable when identity stays the same.
- Stop on ambiguity that risks integrity.
- Do not hide a new artifact inside an old identity.

## Quick Compliance Checklist
- Did the update target the correct artifact?
- Was the structured markdown output updated before derivatives?
- Were only requested sections changed?
- Were unchanged sections and metadata preserved?
- Were stable IDs preserved where possible?
- Was patch metadata recorded?
- Was compatibility impact assessed and recorded?
- Were derivatives regenerated only as needed from canonical state?
- Did rerendering avoid unrelated semantic drift?
- Was lineage preserved and still understandable downstream?
- Is the result honestly still the same artifact?
- If not, was a superseding artifact created instead?
- If anything was ambiguous or structurally risky, did the update stop for clarification?
