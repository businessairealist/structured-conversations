# Project Layout

## Purpose
This file defines the canonical structure of the workspace.

Its purpose is to create consistency, discoverability, reuse, and low-friction chaining between skills, scripts, operators, and downstream artifact consumers. It tells project participants where materials belong, what each area means, and which locations should be treated as authoritative.

## Scope
This file defines folder and file placement semantics for the workspace.

It focuses on structure, directory intent, canonical placement, and how the layout should be interpreted across skills and scripts.

Runtime behavior, root resolution order, bootstrap behavior, and execution rules belong primarily to `workspace-contract.md`.

Schema specifics, naming rules, render behavior, output lifecycle behavior, and evidence normalization details are elaborated in the other shared references.

## Two-Layer Architecture Overview
The architecture has two layers.

The first layer is the plugin installation. This is the reusable system layer that contains shared skills, references, and scripts. It is stable across projects and provides the logic, schemas, guidance, and render/update capabilities used during execution.

The second layer is the workspace. This is the runtime state for one project. It contains that project’s inputs, project-local references, generated artifacts, presentation outputs, run metadata, caches, and temporary working state.

At a structural level, the model is:

- `plugin/` contains reusable logic and shared reference material.
- `project/` contains one project’s mutable state and generated results.

The plugin layer should not be used as the storage location for project runtime outputs. The workspace is the canonical home for mutable project state.

## Standard Project Scaffold
A workspace should provide the following standard scaffold:

```text
project/
├── the output directory
│   ├── recent/
│   ├── by-topic/
│   ├── by-type/
│   └── index.json
├── intake/
├── inputs/
│   ├── source_docs/
│   ├── source_images/
│   ├── notes/
│   └── data/
├── references/
│   └── project_specific/
├── artifacts/
│   ├── shared/
│   ├── foundation/
│   ├── mapping/
│   ├── vision/
│   ├── specification/
│   ├── delivery/
│   ├── quality/
│   ├── strategy/
│   └── index.json
├── outputs/
│   ├── drafts/
│   ├── final/
│   ├── exports/
│   └── index.json
├── runs/
│   ├── manifests/
│   ├── logs/
│   ├── cache/
│   ├── checkpoints/
│   └── latest.json
└── temp/
```

workspace root marker files such as `project.yaml` or `project.json` may also exist at the workspace root and are used for project identification and manifest-level configuration.

## Top-Level Directory Semantics
`intake/` is the landing area for raw request context and newly gathered material that has not yet been normalized into a more specific input or artifact location.

`inputs/` is the canonical source-input area for user-supplied or upstream source material. It is for documents, images, notes, and data that enter the project as source material rather than generated artifacts.

`references/project_specific/` is the project-local guidance area. It holds project-specific instructions, constraints, policies, and context that apply to this project without changing shared plugin references.

`artifacts/` is the reusable generated-artifact area. It holds structured outputs that downstream skills can discover, reuse, transform, and update. This is a primary source-of-truth area.

`outputs/` is the presentation-deliverable area. It holds draft, final, and export-ready deliverables intended for review, handoff, or publication. This is generally a derivative area rather than the canonical semantic source of truth.

the output directory is the user-facing discovery area. It projects structured outputs into a simpler browsing model so users can find work by topic, type, status, and recency rather than by backend folder path.

`runs/` is the runtime metadata and operational state area. It supports auditability, recovery, reproducibility, and efficient execution through manifests, logs, cache, and checkpoints.

`temp/` is the transient working area. It may be used during execution for short-lived intermediate material that should not be treated as canonical project state.

In summary:

- Source-of-truth areas are primarily `inputs/`, `references/project_specific/`, and `artifacts/`.
- Derivative or presentation-oriented areas are primarily `outputs/`.
- Operational areas are primarily `runs/` and `temp/`.

## Input Areas
`inputs/source_docs/` is the canonical location for source documents supplied by the user or an upstream system. Examples include PDFs, text exports, specifications from outside the plugin, transcripts, and imported reports.

`inputs/source_images/` is the canonical location for source images supplied by the user or an upstream system. Examples include screenshots, diagrams, scans, mockups, and photos used as evidence or source material.

`inputs/notes/` is the canonical location for source notes. Examples include meeting notes, workshop notes, interviews, analyst notes, and manually prepared context files.

`inputs/data/` is the canonical location for source datasets and structured input files. Examples include CSV files, tables, structured JSON exports, metrics extracts, and similar input material.

These `inputs/` subdirectories are canonical homes for source material. They are not the right location for generated artifacts, derivative presentation outputs, or run metadata.

`intake/` is different from `inputs/`. Use `intake/` for newly arrived or unresolved request context before it has been classified, normalized, or moved into a more stable source-input location. Use `inputs/` when the material is recognized as ongoing source material for the project.

## Artifact Areas
`artifacts/` stores reusable generated artifacts for chaining across skills.

This area is intended for semantic outputs that should remain discoverable and reusable after the producing run finishes. Unless a task is explicitly producing a presentation-only deliverable, structured outputs should live under `artifacts/`.

`artifacts/shared/` is for cross-collection shared material. It is the right location for artifacts or normalized resources that do not belong to exactly one collection or that are designed to support multiple downstream collections.

The collection roots map directly to the plugin collections:

- `artifacts/foundation/`
- `artifacts/mapping/`
- `artifacts/vision/`
- `artifacts/specification/`
- `artifacts/delivery/`
- `artifacts/quality/`
- `artifacts/strategy/`

These collection roots hold structured outputs produced by skills in the corresponding collection. They are the default homes for generated work that should be chainable, versioned, and discoverable by later skills.

## Output Areas
the working directory holds presentation-ready draft deliverables that are intended for review, iteration, or approval.

the working directory holds finalized deliverables that are ready for handoff, publishing, or formal use.

`outputs/exports/` holds export-oriented derivatives such as packaged deliverables, transformed distribution formats, or files created specifically for external transfer.

The key distinction is:

- `artifacts/` holds reusable semantic artifacts for chaining and update.
- `outputs/` holds presentation-ready deliverables for consumption or distribution.

Outputs should not be treated as the canonical semantic source of truth unless an artifact family explicitly defines that behavior. In the workspace-hardened model, the default assumption is that presentation outputs are derivative of structured output state.

## Project-Specific Reference Area
`references/project_specific/` is for project-local guidance, special rules, constraints, glossaries, conventions, and contextual reference material that apply only within the current project.

This area is appropriate for project-specific instructions that shape how skills should behave for this project, such as domain terminology, stakeholder conventions, internal policy notes, or project-level workflow constraints.

It should not be used to modify or replace shared plugin references. Shared plugin references remain authoritative for the reusable plugin system; project-specific references provide local overlay context for one project.

## structured output Placement
structured outputs should generally live under the following structure:

```text
artifacts/<collection>/<skill>/<artifact_slug>/
```

Within each structured output folder, the expected canonical files are:

- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

the structured markdown output is the source of truth.

the human-readable summary is the primary human-readable companion representation.

execution notes records artifact-level build and packaging context.

source traceability notes records lineage and source relationships.

open questions records unresolved issues that remain attached to the output package.

The structured output folder is the stable unit that downstream skills should discover and consume.

## Normalized Evidence Placement
Normalized evidence should live under:

```text
the working directory
```

This area is for normalized forms of evidence that may be reused across multiple skills or collections.

Examples include normalized notes, extracted interview snippets and quotes, normalized screenshots and diagrams, metrics tables, and prior generated artifacts that have been transformed into a shared evidence format for downstream use.

## Collection-Specific Artifact Roots
The default collection-to-root mapping is:

- `foundation-routing` -> `artifacts/foundation/` for routing, normalization, format selection, and other foundational text-oriented artifacts.
- `mapping-discovery` -> `artifacts/mapping/` for empathy maps, impact maps, journey maps, value stream maps, story maps, and similar discovery and visualization artifacts.
- `vision-messaging` -> `artifacts/vision/` for elevator pitches, future press releases, audience-adapted messaging, and related narrative artifacts.
- `feature-specification` -> `artifacts/specification/` for feature maps, example maps, epics, acceptance criteria, Gherkin scenarios, and living documentation artifacts.
- `story-delivery` -> `artifacts/delivery/` for user stories, story slices, spikes, sub-task plans, and delivery-planning artifacts.
- `quality-diagnostics` -> `artifacts/quality/` for defect reports, reproduction scaffolds, and other quality and diagnostic artifacts.
- `strategy-experimentation` -> `artifacts/strategy/` for roadmaps, hypotheses, experiment designs, OKRs, OKRIs, and related strategic planning artifacts.

These roots are the default artifact homes for their collections and should be preferred over ad hoc project-specific storage layouts.

## Stable Contract Surfaces vs Internal Implementation Detail
The following paths should be treated as stable contract surfaces for skill authors:

- the standard top-level project scaffold
- `inputs/source_docs/`
- `inputs/source_images/`
- `inputs/notes/`
- `inputs/data/`
- `references/project_specific/`
- `artifacts/shared/`
- the collection roots under `artifacts/`
- structured output folders under `artifacts/<collection>/<skill>/<artifact_slug>/`
- the standard structured output files
- the standard render package locations
- the workspace
- `outputs/index.json`
- the output directory.json`
- `runs/latest.json`
- the run-state roots under `runs/`

The following should generally be treated as internal implementation detail, even if they are visible on disk:

- cache contents inside `runs/cache/`
- transient work products inside `temp/`
- script-specific scratch files that are regenerated during execution
- incidental internal file organization beneath a skill’s private operational workflow, as long as it does not alter the shared contract surfaces

Skill authors should rely on contract surfaces, not on incidental implementation detail. If a path is not part of the shared layout contract, do not assume it is stable across plugin versions, script implementations, or project evolutions.

## Layout Rules for Skill Authors
Use the standard scaffold and collection roots first.

Do not write structured outputs into `inputs/`.

Do not treat `outputs/` as the canonical source of truth unless the artifact family explicitly says so.

Do not scatter run metadata outside `runs/`.

Do not create ad hoc top-level folders without updating the shared layout references.

Prefer collection roots and registry-based discovery over hardcoded file paths.

Write reusable generated artifacts under `artifacts/` unless the request is explicitly for a presentation-only deliverable.

Keep project-local contextual guidance in `references/project_specific/`, not inside shared plugin references.

Place visual renders inside the owning artifact folder rather than in a detached global render directory.

Preserve layout stability during updates. Update the structured markdown output package first, then regenerate derivative render or output files as needed.

## Relationship to Other Shared References
`workspace-contract.md` defines execution behavior for working inside the workspace, including root resolution, bootstrap expectations, independent invocation behavior, and writeback expectations.

`artifact-location-rules.md` defines the more detailed placement logic used when selecting exact artifact destinations within the layout.

`artifact-naming-conventions.md` defines how artifact folders, files, and slugs should be named so discovery remains predictable.

`artifact-schema.md` defines structured output structure and field expectations.

`render-contract.md` defines render families, default render targets, optional Mermaid use, and render package expectations.

`artifact-lifecycle.md` defines versioning, compatibility, staleness, supersession, and update-related lifecycle rules.

`evidence-normalization.md` defines how source evidence should be normalized and represented for reuse across skills.

This file should be used when deciding where things belong. The companion references should be used when deciding how those things behave, how they are named, how they are rendered, and how they evolve over time.

## Quick Compliance Checklist
- Does the project use the standard top-level scaffold?
- Are source documents, images, notes, and data stored under `inputs/` rather than mixed into artifacts or outputs?
- Are project-local rules stored under `references/project_specific/`?
- Are reusable generated artifacts stored under the correct `artifacts/<collection>/` root?
- Does each structured output live in its own artifact folder with the standard canonical files?
- Is the structured markdown output treated as the source of truth?
- Are visual renders stored inside the owning artifact folder under `render/`?
- Are draft, final, and export deliverables stored under `outputs/` rather than mixed into structured output locations?
- Is the output directory available as the human-facing browse layer so users can find artifacts without navigating nested backend folders directly?
- Are manifests, logs, cache, and checkpoints kept under `runs/`?
- Are registry and latest-run files used for discovery instead of ad hoc path assumptions?
- Does the skill avoid creating ad hoc top-level folders or scattering metadata outside the shared layout?
