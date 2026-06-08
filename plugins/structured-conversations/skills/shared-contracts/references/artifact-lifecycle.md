# output lifecycle

## Purpose
This file defines how structured outputs evolve over time.

Its purpose is to make artifact change safe, traceable, and reusable across the workspace. The lifecycle contract exists so skills and scripts can preserve lineage, resolve compatibility-aware dependencies, control change, and avoid unsafe reuse.

The intended result is safe reuse, clear lineage, compatibility-aware chaining, and controlled change across all collections and artifact families.

## Scope
This file governs lifecycle behavior for structured outputs and the interpretation of compatibility during creation, update, supersession, reuse, staleness handling, and recomputation.

It applies across collections, artifact families, runtime profiles, and independently invoked skills.

This file does not redefine schema shape, file placement, naming, rendering structure, or full runtime orchestration. Those concerns are owned by sibling shared references.

## Relationship to Other Shared References
`workspace-contract.md` defines how skills resolve the workspace root, search standard locations, write outputs, update indexes, and record runs.

`artifact-schema.md` defines the structured markdown output package, required files, required fields, and schema-level structure.

`artifact-location-rules.md` defines where artifacts live in the workspace and how artifact paths are resolved.

`artifact-naming-conventions.md` defines deterministic naming, slugs, and naming consistency rules.

`render-contract.md` defines render targets, render package expectations, and renderer-family behavior.

`update-integrity-rules.md` defines how updates preserve integrity at the field, node, section, and render level.

This file complements those references by defining how artifacts change over time, when they remain reusable, when they become unsafe to reuse, and how downstream skills must interpret lifecycle metadata.

## Lifecycle Principles
The following rules are mandatory lifecycle principles for structured outputs:

- Artifacts are versioned and must not be silently replaced.
- A new artifact may declare `supersedes_artifact identifier` when it semantically replaces an earlier artifact.
- Downstream skills and scripts must resolve the latest compatible artifact, not merely the newest artifact.
- Artifacts must be marked stale when upstream changes affect safe downstream reuse or compatibility.
- Every update run must record the requested change, changed fields, untouched fields, and compatibility impact.
- structured output content is the source of truth. Renders and exports are downstream derivatives.
- Updates must preserve data integrity and must only alter the requested parts.
- Lifecycle metadata must remain explicit enough for both human review and automated resolution.
- Every skill may be called independently and therefore must evaluate lifecycle state and compatibility each time it selects or updates an artifact.

## Core Lifecycle States
Lifecycle state exists to support reuse decisions, not just description. Each structured output must have a status that reflects its dominant lifecycle condition.

### `draft`
The artifact exists as a canonical package but is not yet the trusted reusable version for downstream chaining.

Operational meaning:
- It may be incomplete, provisional, or awaiting review.
- It may be referenced for inspection.
- It must not be selected automatically when a current compatible artifact exists.

### `current`
The artifact is the active canonical version for its semantic identity and may be reused when compatible.

Operational meaning:
- It is the normal candidate for downstream resolution.
- It is still subject to compatibility checks.
- Current does not mean universally reusable.

### `superseded`
The artifact has been semantically replaced by a newer structured output, typically linked through `supersedes_artifact identifier` on the newer artifact.

Operational meaning:
- It remains part of project history.
- It may still be inspected or referenced for audit and lineage.
- It must not be auto-selected when the superseding artifact is compatible and available.

### `stale`
The artifact is no longer safely reliable for blind reuse because upstream changes, invalidated assumptions, broken evidence, or downstream expectations have affected it.

Operational meaning:
- It may still contain useful information.
- It must not be silently reused without explicit staleness handling.
- `stale_reason` must explain why reuse is unsafe.

### `incompatible`
The artifact is not fit for a specific downstream use, target family, schema expectation, or chaining context.

Operational meaning:
- It may still be current for another use.
- It must not be used for the incompatible context.
- Compatibility metadata must make the incompatibility understandable.

### `archived`
The artifact is retained for recordkeeping, lineage, or audit purposes and is outside normal resolution flow.

Operational meaning:
- It is not a normal candidate for downstream reuse.
- It remains discoverable for history and traceability.
- It must not be revived silently as the active source of truth.

When a single status value cannot express the full situation, status must reflect the dominant lifecycle state and the remaining lifecycle and compatibility facts must be expressed through fields such as `compatible_with`, `stale_reason`, and `recompute_required_for`.

## Artifact Creation Rules
Creation means establishing a new structured output package with its own semantic identity in the workspace.

A skill must create a new structured output package when any of the following is true:

- No existing structured output matches the requested semantic target.
- The requested output introduces a new semantic identity, scope, artifact family, or downstream interpretation.
- The safer path is to preserve the existing artifact untouched and create a separately traceable result.
- The requested change materially alters what the artifact is, not just what it currently says.

Creation of a structured output requires all of the following:

- The canonical package exists under the correct artifact root.
- Required canonical files are created.
- Lineage is initialized in canonical metadata and provenance.
- Source artifacts, inputs, assumptions, and traceability are recorded.
- The artifact is registered so downstream skills can discover it through the workspace.
- A execution record is written for the creation run.

Creation is not complete when only a render, export, or draft deliverable exists. Creation establishes canonical identity first and render derivatives second.

## Artifact Update Rules
An update means modifying an existing structured output while preserving its semantic identity.

A change qualifies as an update only when the artifact still represents the same underlying thing after the change. If the meaning, scope, or intended downstream interpretation materially changes, the operation is not a true update and should be treated as a new artifact or superseding artifact.

All true updates must follow these rules:

- Preserve the existing semantic identity.
- Preserve stable identity fields when the artifact remains the same artifact.
- Update canonical content before regenerating downstream renders.
- Record what changed and what remained untouched.
- Preserve provenance, lineage continuity, and traceability to upstream artifacts actually used.
- Record compatibility impact for downstream consumers.
- Update registry and run-manifest records after a successful update.

Every update run must capture, at minimum:

- requested change
- changed fields
- untouched fields
- compatibility impact

Where the artifact family or update rules support patch recording, the update should also capture:

- `requested_patch`
- `applied_patch`
- `preserved_sections`
- whether downstream render output was regenerated

## Supersession Rules
Supersession means creating a newer structured output that replaces an earlier artifact semantically while preserving lineage between them.

Supersession must be used when a request produces a result that is best represented as a new structured output rather than an in-place update, but where the new artifact clearly replaces an earlier artifact in the same conceptual chain.

A superseding artifact should declare `supersedes_artifact identifier` when it replaces a prior artifact semantically.

Supersession is usually the correct choice when any of the following is true:

- Scope changes materially.
- Interpretation changes materially for downstream skills.
- Identity-preserving update would obscure a major semantic replacement.
- A new baseline is needed while retaining the full prior artifact history.
- The old artifact should remain inspectable and auditable exactly as it was.

Supersession rules:

- The prior artifact must remain intact.
- Supersession must not erase prior history, provenance, or registry presence.
- The prior artifact should normally be marked `superseded` rather than deleted.
- The new artifact becomes the preferred candidate only if it is compatible for the downstream use.
- Downstream resolution must still respect compatibility, not just recency.

## Compatibility Rules
Compatibility is fitness for safe downstream reuse in a given context.

Compatibility is not a general statement that an artifact is good or bad. It is a context-specific decision about whether a downstream skill or script can safely rely on the artifact for a particular purpose.

Compatibility evaluation must consider all relevant lifecycle and compatibility metadata, including:

- `compatible_with`
- `stale_reason`
- `recompute_required_for`
- `partial_update_supported`
- `supersedes_artifact identifier`

Compatibility may depend on:

- schema version expectations
- artifact family expectations
- intended downstream use
- collection-specific requirements
- lineage integrity and traceability completeness
- whether upstream dependencies or evidence remain valid
- whether the artifact has been superseded, marked stale, or otherwise disqualified for the target use

An artifact may be `current` and still be incompatible for a specific downstream skill.

An artifact may also remain useful for one downstream path while requiring recomputation for another.

Compatibility must be treated as unsafe when required lifecycle metadata is missing, ambiguous, or contradictory.

## Latest-Compatible Resolution Rules
Latest-compatible is the required reuse rule.

Newest by timestamp alone is insufficient and must not be treated as a valid reuse rule.

Unless a request explicitly overrides normal resolution, skills and scripts must use the following decision order:

1. Use the explicit path or specific artifact requested by the user, if it exists and is safe for the requested use.
2. Otherwise use an explicit alias, manifest pointer, or registry pointer that resolves to a safe artifact.
3. Otherwise search standard locations and registry entries for the latest artifact that is still compatible and not disqualified by staleness, incompatibility, or unresolved supersession.
4. If no artifact is safely compatible, create, recompute, or request clarification according to the runtime contract and the safety of the decision.

Resolution must not auto-select an artifact that is:

- stale with unresolved impact
- incompatible for the requested downstream use
- ambiguously superseded
- missing lifecycle metadata required for safe selection

If compatibility cannot be safely determined, the skill must stop and ask rather than guess.

## Staleness Rules
Staleness is loss of safe reliability for blind reuse.

An artifact is stale when upstream changes, broken assumptions, invalidated evidence, lineage drift, or changed downstream expectations mean the artifact can no longer be trusted without review or recomputation.

Stale does not always mean useless. It means the artifact must not be reused blindly.

Artifacts should be marked stale when any of the following occurs:

- an upstream source artifact changes in a way that affects meaning, structure, or dependent fields
- evidence the artifact depends on is invalidated, replaced, or no longer current enough for the target use
- a schema or artifact-family expectation changes and the artifact has not been reconciled
- a downstream expectation known to the artifact contract is no longer met
- a partial update to an upstream artifact invalidates assumptions in dependent artifacts

`stale_reason` must explain the cause of staleness in terms that both scripts and humans can act on. It should identify what changed, why that matters, and what kind of follow-up is likely required.

Marking an artifact stale is preferred over silent reuse, silent deletion, or silent mutation.

## Recompute Requirement Rules
`recompute_required_for` expresses which downstream uses, artifact families, or dependency paths must be regenerated when the artifact becomes stale or incompatible.

This field exists to support targeted automation and safe reuse decisions.

Recompute requirements must be specific enough to answer the question: what downstream work is no longer safe to trust as-is?

Good recompute requirements identify one or more of the following:

- downstream artifact families
- downstream skill types
- named dependency chains
- specific derivative artifacts
- known render or transform outputs that must be regenerated

Recomputation rules:

- Not every update requires full recomputation of every downstream derivative.
- Recompute scope should be limited to the downstream uses actually affected.
- When only render derivatives are affected, recompute may stop at rerender.
- When canonical meaning changes, downstream structured outputs may need regeneration as well as rerendering.
- If the recompute scope cannot be safely bounded, the skill must escalate rather than under-recompute.

## Partial Update vs New Artifact Rules
Three distinct lifecycle actions must be treated differently.

### Safe in-place partial update
A safe in-place partial update changes only requested parts of an existing artifact while preserving the same semantic identity.

This is allowed only when all of the following are true:

- `partial_update_supported` is true for the artifact or artifact family
- semantic identity remains the same
- unchanged content can remain intact without reinterpretation
- lineage and compatibility remain understandable after the patch
- the change does not functionally replace the artifact with a different one

### Substantive update that preserves identity
A substantive update changes meaningful content but still preserves the same semantic identity.

This is appropriate when the artifact remains the same artifact, but important canonical fields need revision. It still requires explicit change recording, compatibility evaluation, and downstream impact assessment.

### New superseding artifact
A new superseding artifact is required when the request materially changes identity, scope, downstream meaning, or safe interpretability.

This is the safer path when in-place update would hide a major semantic replacement.

Partial updates must not be used to hide major semantic replacement.

When identity, scope, or downstream interpretation changes materially, a new artifact or superseding artifact is usually the correct choice.

## Downstream Reuse Rules
Downstream skills must prefer valid compatible artifacts over unnecessary regeneration.

Downstream skills must evaluate lifecycle and compatibility before reuse, even when the artifact appears recent or comes from a normal location.

When selecting upstream artifacts, downstream skills must:

- resolve using latest-compatible logic
- reject timestamp-only selection
- inspect staleness and incompatibility signals
- preserve lineage back to the specific upstream artifact actually used
- record the selected upstream artifact in canonical traceability and run metadata

Downstream skills must not silently reuse artifacts that are:

- stale with unclear impact
- incompatible for the requested use
- ambiguously superseded
- missing lifecycle metadata required for safe selection

When an artifact is stale, incompatible, or ambiguous, the downstream skill must do one of the following:

- select another compatible artifact
- recompute the needed artifact path
- ask for clarification when multiple safe interpretations remain

Transformed artifacts must preserve lineage to the exact upstream artifact version actually used, not just to an artifact family or alias.

## Stability Expectations Across Updates
When artifact identity has not changed, stability is required.

The following should remain stable across a true in-place update whenever applicable:

- artifact identifier
- unchanged content sections
- stable node or element IDs
- provenance and lineage continuity
- deterministic file naming
- deterministic placement under the workspace rules

The following may legitimately change during a valid update:

- `updated_at`
- `status`
- changed semantic fields
- compatibility metadata
- downstream render derivatives after valid rerender
- run-manifest and registry references needed to reflect the new update event

Stability is required because downstream tools, human reviewers, diffs, references, and automation depend on it. Identity-preserving updates must remain recognizable as the same artifact with controlled changes.

## Failure and Clarification Rules
A skill must stop and ask for clarification when any of the following is true:

- multiple plausible upstream artifacts match the request
- compatibility cannot be determined safely
- an artifact is stale and the impact on the requested operation is unclear
- the request is ambiguous about updating an existing artifact versus creating a new one
- required lifecycle metadata is missing, contradictory, or too incomplete for a safe decision
- the requested change would invalidate schema expectations, break lineage, or create ambiguous structural change

A skill may proceed automatically when all of the following are true:

- one artifact is the clearly intended target or dependency
- lifecycle metadata is present and internally consistent
- compatibility is affirmatively satisfied for the requested use
- the requested operation fits the artifact’s update and integrity rules
- downstream impact is understood well enough to record and handle safely

A skill must refuse to guess when guessing would risk:

- data integrity
- lineage accuracy
- downstream correctness
- unsafe reuse of stale or incompatible artifacts
- silent semantic replacement of one artifact by another

## Non-Negotiable Rules
- No structured output may be silently replaced.
- Every structured output must be versioned.
- `supersedes_artifact identifier` must be supported for semantic replacement.
- Latest-compatible takes precedence over latest-by-time.
- Stale artifacts must be marked when upstream changes invalidate safe reuse.
- Compatibility must be evaluated for the actual downstream use, not assumed globally.
- Every update must record the requested change, changed fields, untouched fields, and compatibility impact.
- Identity-preserving updates must preserve stable identifiers and unchanged content where applicable.
- Canonical content must be updated before downstream renders are regenerated.
- Missing lifecycle metadata is a safety problem, not a minor omission.

## Quick Compliance Checklist
- Does the artifact remain canonical and fully packaged?
- Is the operation correctly classified as create, update, or supersede?
- Was any semantic replacement handled without silent overwrite?
- Was `supersedes_artifact identifier` used where semantic replacement occurred?
- Was compatibility evaluated for the actual downstream use?
- Did selection follow latest-compatible rather than latest-by-time?
- Were stale conditions checked and `stale_reason` recorded when needed?
- Was `recompute_required_for` updated when downstream regeneration is required?
- Were requested change, changed fields, untouched fields, and compatibility impact recorded?
- Were stable identifiers, unchanged sections, and lineage preserved where identity did not change?
- Were registry and run-manifest records updated after success?
- Did the skill stop instead of guessing when lifecycle safety was unclear?
