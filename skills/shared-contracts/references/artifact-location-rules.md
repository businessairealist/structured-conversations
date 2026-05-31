# Artifact Location Rules

## Purpose
This file defines where artifacts should live and how they should be found.

Its goal is to enforce consistency, discoverability, safe reuse, and reliable chaining between skills. Skills, scripts, and humans should be able to resolve the correct artifact without ad hoc path hunting or competing source-of-truth copies.

## Scope
This file governs placement and lookup rules for artifacts and closely related files inside the workspace.

`project-layout.md` defines the project structure. This file defines the operational rules for using that structure.

`workspace-contract.md` defines the broader runtime contract for resolving the workspace root, loading context, executing a skill, and writing run records. This file does not replace that contract.

## Relationship to Project Layout and workspace conventions
`project-layout.md` answers: what standard directories and index files exist in the workspace.

`workspace-contract.md` answers: how skills resolve the workspace root, bootstrap missing scaffold pieces, and behave when called independently.

This file answers two narrower questions:
- where things go
- how to find them safely

Use this file whenever a skill or script needs to decide whether a file belongs under `artifacts/`, `outputs/`, `runs/`, `references/`, or `inputs/`, and whenever it needs to choose the correct upstream artifact.

## Artifact Classes
### Source inputs
Source inputs are original materials provided to the project. They are not generated structured outputs.

Typical locations:
- `intake/`
- `inputs/source_docs/`
- `inputs/source_images/`
- `inputs/notes/`
- `inputs/data/`

Role: source material.

Source-of-truth status: authoritative for the original input only.

### structured outputs
structured outputs are the primary generated project artifacts that downstream skills should consume.

Typical location:
- `artifacts/<collection_root>/<skill>/<artifact_slug>/`

Required package files:
- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

Role: durable semantic output for reuse, transformation, validation, and chaining.

Source-of-truth status: yes. the structured markdown output is the semantic source of truth.

### Rendered artifacts
Rendered artifacts are derivative human-facing renders generated from canonical content.

Typical location:
- inside the structured markdown output folder

Examples:

Role: presentation of canonical content.

Source-of-truth status: no. Rendered files are derivatives.

### Presentation outputs
Presentation outputs are delivery-oriented files written for review, distribution, or external consumption.

Typical location:
- the working directory
- the working directory
- `outputs/exports/`

Role: formatted deliverables and exports.

Source-of-truth status: no. They must point back to a structured output when one exists.

### Normalized evidence
Normalized evidence is reusable intermediate evidence derived from source inputs or prior artifacts.

Typical location:
- the working directory

Examples:
- normalized notes
- normalized quotes
- normalized screenshot observations
- normalized metrics tables
- normalized upstream artifact extracts

Role: reusable intermediate evidence for later skills.

Source-of-truth status: no. It is an operational derivative of source material.

### Runtime metadata
Runtime metadata records execution details, manifests, logs, cache, and checkpoints.

Typical location:
- the working directory
- `runs/logs/`
- `runs/cache/`
- `runs/checkpoints/`
- `runs/latest.json`

Role: execution trace, runtime support, and recovery.

Source-of-truth status: operational only.

### Project-specific references
Project-specific references are local guidance or reference documents that help shape artifact generation but are not themselves canonical generated artifacts.

Typical location:
- `references/project_specific/`

Role: contextual reference material.

Source-of-truth status: reference only. They do not replace structured outputs or source inputs.

## Default Collection Roots
Canonical generated artifacts belong under these default collection roots:

- `foundation-routing` -> `artifacts/foundation/`
- `mapping-discovery` -> `artifacts/mapping/`
- `vision-messaging` -> `artifacts/vision/`
- `feature-specification` -> `artifacts/specification/`
- `story-delivery` -> `artifacts/delivery/`
- `quality-diagnostics` -> `artifacts/quality/`
- `strategy-experimentation` -> `artifacts/strategy/`

These are the default homes for canonical generated artifacts. A skill should write to its collection root unless a documented exception exists.

Shared reusable evidence belongs under `artifacts/shared/`, not under a collection root.

## structured output Placement Rules
The standard canonical folder pattern is:

`artifacts/<collection_root>/<skill>/<artifact_slug>/`

Examples:
- the working directory
- the working directory
- the working directory

Every structured output folder must contain:
- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

Rules:
- the structured markdown output is the semantic source of truth.
- the human-readable summary is the primary human-readable representation of the same artifact.
- Skills must not scatter canonical files directly at the collection root unless a documented exception exists.
- structured outputs belong under `artifacts/`, never under `outputs/`.
- structured outputs must be organized under the producing skill so downstream lookup can stay narrow and deterministic.
- Canonical folders should be stable across partial updates. Do not create a new location for the same artifact unless lifecycle rules require a new structured output.

## Rendered Artifact Placement Rules
Rendered files belong inside the structured markdown output folder, not in a separate competing source-of-truth location.

Standard render placement for artifacts that support structured rendering:

Rules:
- Rendered files are derivatives of canonical content.
- HTML is the default visual render target.
- Mermaid is optional and must be omitted when it cannot faithfully represent the artifact.
- Regenerated renders replace older renders in the same canonical folder unless lifecycle rules explicitly require a new structured output.
- Rendered files must never become the only surviving representation of an artifact.

For non-visual artifacts, the human-readable summary is usually the primary human-readable output and a `render/` subtree may be omitted unless a skill explicitly generates one.

## Draft, Final, and Export Placement Rules
Presentation and delivery files belong under `outputs/`, not under `artifacts/`.

Standard roots:
- drafts -> the working directory
- finals -> the working directory
- exports -> `outputs/exports/`

Recommended organization:
- the working directory<skill>/`
- the working directory<skill>/`
- `outputs/exports/<skill>/`

When a deliverable is tied to a specific structured output, the output should also encode or record that linkage through filename, adjacent metadata, registry entry, or execution record.

Rules:
- Drafts are reviewable presentation outputs.
- Finals are approved or delivery-ready presentation outputs.
- Exports are format conversions or package variants such as `.docx`, `.pdf`, `.csv`, `.feature`, or similar files.
- These locations are for presentation and delivery, not canonical semantic storage.
- Skills may write to them when the request explicitly asks for a draft, final, export, or presentation-ready deliverable.
- Exported files may be linked back to the structured markdown output in execution notes, the output catalog, and the execution record.
- An output file must not become an unofficial source of truth simply because it is easier to open or newer by timestamp.

## Normalized Evidence Placement Rules
Normalized evidence belongs under:

the working directory

Allowed contents include:
- normalized notes
- normalized quotes
- normalized screenshot observations
- normalized metrics tables
- normalized upstream artifact extracts

Rules:
- Normalized evidence is reusable intermediate evidence.
- It is not a substitute for original source inputs.
- Skills may read from normalized evidence when it is compatible with the current request and traceable to its sources.
- Skills should write normalized evidence here when the normalization output is intended for reuse across multiple downstream skills.
- Normalized evidence should preserve traceability back to source inputs or source artifacts.

## execution record and Runtime Metadata Placement Rules
execution records belong under:

the working directory

Related runtime locations:
- logs -> `runs/logs/`
- cache -> `runs/cache/`
- checkpoints -> `runs/checkpoints/`
- latest run pointer -> `runs/latest.json`

Rules:
- Runtime metadata must not be mixed into structured output folders unless it is explicitly part of the structured markdown output package.
- execution notes inside a structured output folder describes that output package.
- execution records in the working directory describe a specific execution event.
- Logs, cache, and checkpoints remain runtime support files and must stay under `runs/`.
- Runtime records should reference structured outputs and outputs by path or identifier rather than duplicating their content.

## Standard Discovery and Lookup Order
When a skill needs inputs or upstream artifacts, it must use this lookup order:

1. explicit path provided in the request
2. explicit artifact identifier or slug provided in the request
3. project manifest aliases and pointers
4. prior run metadata
5. collection-specific standard folders
6. the workspace
7. latest compatible artifact
8. ask the user only if nothing safe and usable is found

Operational rules:
- Search the narrowest valid location first before broadening the search.
- If the request names a path, do not ignore it in favor of a newer registry entry.
- If the request names an artifact identifier or slug, resolve within the correct collection and skill scope before searching more broadly.
- Check project manifest pointers before scanning broad folders when aliases are available.
- Use prior run metadata to recover expected artifact paths when the request is clearly continuing earlier work.
- Search collection-specific standard folders before broad registry fallback.
- Use the workspace as a discovery aid, not as a replacement for compatibility checks.
- The final selected artifact must still pass latest-compatible resolution.

## Latest-Compatible Resolution Rules
Latest compatible is required. Latest by timestamp alone is not sufficient.

Skills must consider compatibility markers including:
- `supersedes_artifact identifier`
- `compatible_with`
- `stale_reason`
- `recompute_required_for`
- `partial_update_supported`

Resolution rules:
- Prefer the newest artifact that is still compatible with the current request and its upstream dependencies.
- Do not select an artifact marked stale for the needed downstream use.
- Do not select an artifact that requires recomputation for the requested downstream action.
- For update operations, confirm that partial update is supported before modifying in place.
- If an artifact supersedes another and remains compatible, prefer the superseding artifact.
- If multiple candidates remain compatible, prefer the narrowest exact match to the requested artifact, then the most recent compatible one.
- If compatibility cannot be safely determined, stop and ask rather than guessing.

## Explicit Path, Alias, and Registry Rules
Explicit paths override broader discovery.

Rules for explicit paths:
- If the request supplies a file path, use that path first.
- If the path resolves to a valid artifact or input, do not silently switch to another candidate.
- If the explicit path conflicts with integrity or compatibility checks, stop and surface the conflict.

Rules for aliases and pointers:
- Project manifest aliases or pointers may identify preferred artifacts, canonical starting points, or named handoff files.
- Aliases may narrow discovery but must not contradict canonical placement rules.
- An alias can point to a structured output, a source input, or a project-specific reference, but it does not redefine where those file classes belong.

Rules for registry-driven lookup:
- The output catalog supports discovery, reuse, and latest-compatible selection.
- Registry entries should point to structured output locations rather than duplicate them.
- Registry entries and aliases must not legitimize files placed in the wrong root.
- If alias, registry, and explicit path signals disagree, explicit path wins first, then a clarification check determines whether the request is safe to continue.

## Transformation and Derived Artifact Placement
Transformed artifacts should normally be written as new structured output folders under the target collection and skill.

Standard pattern:

`artifacts/<target_collection_root>/<target_skill>/<artifact_slug>/`

Rules:
- Preserve provenance and traceability back to source artifacts.
- Record the upstream artifact references in the new canonical package.
- Do not silently overwrite the source artifact when creating a transformed artifact.
- Use a new structured output when the result is a new artifact type, a new target collection output, or a materially different downstream artifact.
- Write presentation-ready deliverables for the transformed artifact under `outputs/` only when requested.

Examples:
- an empathy map translated into an impact map writes a new structured output under `artifacts/mapping/<target_skill>/...`
- a roadmap transformed into an OKRI writes a new structured output under `artifacts/strategy/<target_skill>/...`

## Partial Update Placement Rules
Partial updates modify the structured markdown output in place only when safe and supported.

Rules:
- Apply the update against the structured markdown output first.
- Preserve unchanged sections, stable IDs, metadata, and provenance whenever possible.
- Preserve upstream traceability and canonical folder identity unless lifecycle rules require a replacement artifact.
- Regenerated renders stay in the same structured output folder.
- the human-readable summary, render files, and any derivative package files should be regenerated from the updated canonical content as needed.
- Versioning and lifecycle metadata must still reflect the update properly.
- Update records should capture requested change, changed fields, untouched fields, and compatibility impact.
- If the requested change would invalidate schema, break compatibility, or require ambiguous structural changes, stop and ask for clarification.

## Conflict, Duplication, and Drift Prevention Rules
Skills and scripts must prevent placement patterns that create ambiguity or drift.

Do not allow:
- duplicate structured outputs in multiple roots for the same intended source of truth
- outputs to be mistaken for structured outputs
- ad hoc export files to become unofficial source of truth
- orphaned renders without a matching canonical folder
- stale artifacts to be selected simply because they are newer

Required behavior:
- Prefer reuse of valid compatible artifacts over unnecessary regeneration.
- Keep canonical-under-`artifacts/` and presentation-under-`outputs/` boundaries strict.
- Keep renders under their canonical folder.
- Register new structured outputs and outputs so future discovery does not rely on manual folder inspection.
- Mark stale artifacts appropriately rather than silently leaving them eligible for downstream selection.
- Do not copy the same structured output package into another collection root just to satisfy a downstream skill.
- If a file exists in the wrong root, do not treat that misplacement as an accepted alternate storage model.

## Clarification and Failure Rules
A skill must ask for clarification when any of the following are true:
- multiple plausible artifacts match the request
- upstream candidates are incompatible or stale for the intended use
- required source material is missing
- the request is ambiguous about which artifact should be updated
- explicit path, alias, registry, or prior run signals conflict
- compatibility cannot be safely determined
- the requested update risks breaking integrity, schema, or traceability

A skill may proceed automatically when all of the following are true:
- one artifact or input clearly matches the request
- compatibility is confirmed
- the write location is unambiguous
- the requested operation is supported by the output lifecycle and update rules

A skill must refuse to guess when guessing could corrupt data integrity, break traceability, overwrite the wrong artifact, or cause a presentation file to replace canonical truth.

## Relationship to Other Shared References
Use the shared references together, but keep their boundaries clear:

- `project-layout.md`: defines the standard project scaffold and index file locations.
- `workspace-contract.md`: defines project-root resolution, bootstrap behavior, independent skill behavior, and run-level obligations.
- `artifact-naming-conventions.md`: defines how artifact IDs, slugs, names, and related naming patterns should be formed.
- `artifact-schema.md`: defines the structured markdown output structure and field expectations.
- `render-contract.md`: defines renderer families, render package expectations, and render-target rules.
- `artifact-lifecycle.md`: defines supersession, staleness, compatibility, and version progression rules.
- `update-integrity-rules.md`: defines safe update behavior, preservation rules, and patch recording requirements.
- `evidence-normalization.md`: defines how evidence should be normalized and traced back to source material.

This file should not be used to redefine those concerns. It should be used to place and resolve artifacts consistently within the folder structure they define.

## Non-Negotiable Rules
- Canonical generated artifacts live under `artifacts/`.
- structured output packages use `artifacts/<collection_root>/<skill>/<artifact_slug>/`.
- the structured markdown output is the semantic source of truth.
- Rendered files live under the structured markdown output folder.
- Presentation files under `outputs/` are not the source of truth.
- Normalized evidence lives under the working directory.
- execution records and runtime records live under `runs/`.
- Skills must resolve the latest compatible artifact, not merely the newest artifact.
- Explicit paths override broader discovery.
- Aliases, registry entries, and prior runs help discovery but do not legalize wrong placement.
- Registry entries and execution records must be updated after successful writes.
- Skills must not guess when location ambiguity risks integrity or traceability.

## Quick Compliance Checklist
- Is the file being written under the correct root for its class?
- If it is canonical, is it under `artifacts/<collection_root>/<skill>/<artifact_slug>/`?
- Does the canonical package contain the structured markdown output, the human-readable summary, execution notes, source traceability notes, and open questions?
- If renders exist, are they inside the structured markdown output folder?
- If the artifact is visual, is HTML present by default and Mermaid included only when faithful?
- If the file is a draft, final, or export, is it under `outputs/` rather than `artifacts/`?
- If evidence was normalized for reuse, is it under the working directory?
- Are execution records, logs, cache, and checkpoints under `runs/`?
- Did discovery follow explicit path, explicit identifier, aliases, prior runs, standard folders, registry, then latest-compatible resolution?
- Was the selected upstream artifact latest compatible rather than merely newest?
- If transforming an artifact, was a new canonical folder created under the target collection and skill?
- If partially updating an artifact, was the structured markdown output updated first and unchanged content preserved?
- Were registry entries and execution records updated after the write?
- Did the skill stop instead of guessing where ambiguity would risk integrity?
