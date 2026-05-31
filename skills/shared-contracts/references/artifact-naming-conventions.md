# Artifact Naming Conventions

## Purpose
This file defines the canonical naming system for artifacts and related files in the plugin.

The goal is consistency, discoverability, traceability, and low-friction chaining between skills. A name should help humans find the right thing quickly and help scripts resolve the right thing safely.

## Scope
This file governs names and identifiers. It does not govern folder placement, runtime orchestration, or artifact schema design.

It applies to:
- collection names
- skill slugs
- artifact slugs
- artifact folder names
- canonical file names inside artifact folders
- render package file names
- draft, final, and export file names
- execution record names and related runtime file names
- aliases and registry pointers
- human-facing titles and labels

## Relationship to Layout, Location, and Schema References
This file complements the shared references that define structure, placement, execution, and metadata.

- `project-layout.md` defines the standard project scaffold and directory structure.
- `artifact-location-rules.md` defines where artifacts, outputs, and runtime records live.
- `workspace-contract.md` defines how skills resolve the workspace root, locate inputs, and execute independently.
- `artifact-schema.md` defines artifact metadata and field semantics.

This file focuses on what things are called. It does not redefine where they live or how they execute.

## Naming Object Types
### Collection names
Collection names are stable contract values for the major skill groupings. They are machine-facing and human-readable.

Examples:
- `foundation-routing`
- `mapping-discovery`
- `vision-messaging`

### Skill slugs
A skill slug is the canonical machine-facing name for a skill. It appears in skill paths, output roots, and execution record names.

Example:
- `syntax-pattern-selector`

### Artifact slugs
An artifact slug is the canonical machine-facing folder name for one artifact instance under a skill’s artifact root.

Example:
- `checkout-abandonment-analysis`

### Artifact IDs
An artifact ID is the canonical metadata identifier recorded inside the artifact payload. It is machine-facing. It is distinct from the artifact slug.

The slug names the folder. The artifact ID identifies the artifact record.

### File names
File names are the canonical names of files inside artifact folders, render packages, outputs, and runtime records. Some are fixed contract names and some are generated from stable naming rules.

### execution record names
A execution record name is the filename for a runtime record written for a single execution. It is machine-facing and audit-oriented.

### Aliases and pointers
Aliases and pointers are human-meaningful convenience names used in project manifests, registries, or operator workflows to locate structured outputs. They are both machine-usable and human-facing.

### Human-facing titles
A human-facing title is display text intended for people reading artifacts, outputs, or interfaces. It is not a canonical identifier.

### Render target names
Render target names describe supported derivative output forms such as `html`, `mermaid`, `svg`, `preview`, or `markdown`. They are both machine-facing and human-readable.

## General Naming Rules
- Use lowercase by default for machine-facing names.
- Use kebab-case for slugs.
- Prefer stable names over clever names.
- Prefer semantic meaning over implementation trivia.
- Keep names deterministic across rerenders, rebuilds, and partial updates.
- Do not embed transient presentation state in canonical names.
- Do not encode temporary workflow status into canonical identifiers.
- Do not make file names carry meaning that belongs in metadata.
- Use naming rules that support compatibility resolution, traceability, and safe automation.

Good machine-facing names describe what something is. They should not depend on who rendered it, which UI displayed it, or which temporary branch of work produced it.

## Collection Naming Rules
The collection IDs are stable contract values:
- `foundation-routing`
- `mapping-discovery`
- `vision-messaging`
- `feature-specification`
- `story-delivery`
- `quality-diagnostics`
- `strategy-experimentation`

Do not casually rename collection IDs. They are shared reference points across skills, scripts, manifests, and registries.

Directory names under `artifacts/` use shorter canonical roots:
- `foundation`
- `mapping`
- `vision`
- `specification`
- `delivery`
- `quality`
- `strategy`

Collection IDs and directory roots are related but not interchangeable in every context.

Examples:
- Collection ID: `feature-specification`
- Artifact directory root: `artifacts/specification/`

Use the collection ID when referring to the collection as a logical contract surface. Use the directory root when referring to the physical artifact location defined by the project layout and location rules.

## Skill Slug Naming Rules
Skill slugs must use lowercase kebab-case.

Skill slugs should be descriptive, stable, and action-oriented when appropriate.

Examples:
- `verb-noun-rewriter`
- `syntax-pattern-selector`
- `empathy-map-builder`
- `gherkin-scenario-writer`

Skill paths must align with the slug:

`skills/<skill-slug>/SKILL.md`

Rules:
- A skill slug must remain stable once published.
- A skill slug must not change just because marketing copy, display copy, or chapter wording changes.
- A skill slug should not include a collection prefix unless it is required for uniqueness.
- A skill slug should not include file-format terms such as `html`, `json`, or `mermaid` unless format conversion is the actual semantic purpose of the skill.
- A skill slug should not include version numbers unless the version is part of a long-lived compatibility contract.

Preferred pattern:
- `<action>-<object>`
- `<artifact>-<action>`
- `<concept>-<role>`

Examples:
- Good: `impact-map-builder`
- Good: `invest-readiness-checker`
- Avoid: `mapping-impact-map-builder-v2`

## Artifact Slug Naming Rules
The artifact slug is the canonical folder name under a skill’s artifact root.

Artifact slugs must use lowercase kebab-case.

Artifact slugs must be deterministic from the artifact’s semantic purpose, not random, unless a uniqueness suffix is required to prevent a collision.

Artifact slugs should be short but specific enough to distinguish multiple artifacts of the same type.

Recommended pattern:
- `<subject-or-entity>-<purpose-or-focus>`
- optionally add `-<scope>`
- optionally add `-<timeframe>`
- optionally add a deterministic uniqueness suffix when collisions would otherwise occur

Examples:
- `checkout-conversion-impact-map`
- `busy-parent-empathy-map`
- `weeknight-orders-roadmap-q3-2026`
- `discount-eligibility-gherkin-scenarios`

Rules:
- The artifact slug names the artifact folder. It is not a display title.
- The artifact slug must not encode volatile render state such as `html-only`, `latest-preview`, `draft-layout-2`, or similar transient details.
- The artifact slug must remain stable across partial updates when the artifact identity has not changed.
- The artifact slug should only change when the artifact itself becomes a materially different structured output.
- When uniqueness is required, prefer a deterministic disambiguator tied to scope, timeframe, source, or other stable context.
- Use a random suffix only as a last resort.

Examples of deterministic disambiguation:
- `busy-parent-empathy-map-mobile-app`
- `busy-parent-empathy-map-restaurant-kiosk`
- `busy-parent-empathy-map-2026-q2`

## structured output File Naming Rules
Canonical file names inside each artifact folder are fixed:
- the structured markdown output
- the human-readable summary
- execution notes
- source traceability notes
- open questions

These file names are stable contract surfaces. They must not be renamed per skill, per artifact family, or per operator preference.

Rules:
- Semantic differentiation belongs in metadata, not in canonical file renaming.
- Do not create skill-specific substitutions such as `impact-map.json`, `story.md`, or `proof-of-work.json` in place of the canonical files.
- the structured markdown output remains the source of truth.
- the human-readable summary is the primary human-readable markdown artifact when present.

If a skill needs additional derivative or support files, those files must not replace or rename the canonical set.

## Render File Naming Rules
When a render package is present, the standard render-related names are fixed:

These are derivative file names and must remain consistent across visual artifact families.

Rules:
- Keep render package names consistent even when renderer internals differ.
- The presence or absence of Mermaid is based on representational fidelity, not naming preference.
- Do not rename `index.html` to encode artifact meaning. The artifact meaning already exists in the containing structured output folder.
- Do not rename `diagram.mmd`, `diagram.svg`, or `preview.png` per artifact.
- Do not treat render file names as canonical identifiers.

The structured output folder provides identity. The render package provides stable derivative paths.

## Draft, Final, and Export Naming Rules
Files written to the working directory, the working directory, and `outputs/exports/` must be human-legible and traceable back to the structured markdown output.

Recommended pattern:

`<artifact-slug>__<deliverable-kind>.<ext>`

Examples:
- `checkout-conversion-impact-map__facilitation-pack.md`
- `busy-parent-empathy-map__stakeholder-summary.pdf`
- `weeknight-orders-roadmap-q3-2026__exec-brief.html`

Rules:
- Use the artifact slug as the primary identity anchor.
- Use `deliverable-kind` to describe what the output is for humans.
- File-format suffixes belong in the extension, not in the slug.
- Export file names may include a format-relevant suffix only when it adds clarity.
- Output file names must not become the semantic source of truth.
- The structured output folder and the structured markdown output remain the source of truth.

Additional guidance:
- The containing directory already conveys lifecycle stage, so avoid redundant names like `__draft` inside the working directory unless an external consumer requires it.
- If multiple files of the same deliverable kind must coexist, add a deterministic disambiguator after the deliverable kind.

Examples:
- `busy-parent-empathy-map__workshop-board.html`
- `busy-parent-empathy-map__workshop-board-team-a.html`

## execution record and Runtime File Naming Rules
execution records must use a stable, predictable, sortable pattern consistent with the inventory:

`{timestamp}__<skill-slug>.json`

Example:
- `20260420T225238Z__syntax-pattern-selector.json`

Rules:
- Timestamp formatting must be sortable in plain string order.
- Prefer UTC timestamps in compact ISO-like form without spaces or filesystem-hostile characters.
- A execution record name must identify the execution time first and the skill second.
- execution record names must be machine-friendly and audit-ready.

Related runtime records such as logs, cache files, and checkpoints should also favor deterministic machine-friendly naming.

Guidance:
- Per-run records should typically start with the same sortable timestamp and skill slug.
- Reusable cache records should prefer deterministic names derived from stable inputs, artifact identifiers, or normalized keys.
- Do not use ad hoc friendly names for runtime records that need replay, audit, or traceability.

Examples:
- `20260420T225238Z__syntax-pattern-selector.log`
- `20260420T225238Z__syntax-pattern-selector__checkpoint.json`
- `resolve-latest-compatible-artifact__foundation-routing.cache`

## Human-Facing Titles and Labels
Human-facing titles and labels are for readability. They are not canonical identifiers.

A title may use spaces, capitalization, punctuation, and clearer prose.

Examples:
- Slug: `busy-parent-empathy-map`
- Title: `Busy Parent Empathy Map`

Rules:
- Titles and labels may change for readability without changing slugs or canonical IDs.
- Human-facing names should remain semantically aligned with the underlying artifact.
- A title must not imply a different artifact identity than the canonical metadata.
- Display text should help humans understand the artifact, not override the artifact contract.

Use titles for interfaces, reports, and human-readable documents. Use slugs and IDs for paths, linking, and automation.

## Alias and Pointer Naming Rules
Aliases and pointers are convenience names used in project manifests, registries, or operator workflows to refer to structured outputs.

Aliases should be simple, human-meaningful, and conflict-free.

Examples:
- `current-roadmap`
- `latest-epic`
- `checkout-map`

Rules:
- An alias is a pointer, not a replacement for the canonical identifier.
- An alias must not conflict with a canonical skill slug or artifact slug in the same scope.
- An alias must not point ambiguously to multiple active artifacts.
- If an alias changes target, the alias changes, not the canonical slug of the artifact.
- Use aliases to improve operator convenience, not to create a parallel naming system.

Prefer aliases that express role or recency clearly:
- Good: `latest-compatible-roadmap`
- Good: `current-checkout-gherkin`
- Avoid: `roadmap-final-real`

## Transformation, Supersession, and Version Naming Rules
Transformed artifacts and superseding artifacts normally become new structured output folders rather than silently renaming prior folders.

Supersession and compatibility belong in metadata first, not in ad hoc file naming tricks.

Rules:
- Do not silently rename an existing structured output folder to indicate a new version.
- Do not use file name hacks like `artifact-final-final.json` or `story-v3-latest.md` as a substitute for lifecycle metadata.
- Use metadata fields such as version, compatibility, and supersession references to represent lineage.
- Keep prior structured outputs discoverable when they remain relevant for traceability.
- Create a new artifact slug when the semantic identity materially changes.
- Keep the existing artifact slug when the artifact identity is unchanged and the update is a legitimate partial update or revision.

Version numbers belong in metadata unless a file-format or external delivery convention explicitly requires otherwise.

## Ambiguity and Collision Prevention Rules
Naming must prevent avoidable ambiguity.

Do not allow:
- two active artifacts with indistinguishable slugs in the same lookup scope
- output file names that cannot be traced back to structured outputs
- aliases that point ambiguously
- renamed render files that break downstream expectations

Rules:
- Prefer deterministic disambiguators when collisions are unavoidable.
- Prefer scope, subject, timeframe, or stable source context over arbitrary suffixes.
- If two artifacts would otherwise receive the same slug, resolve the conflict before writing files.
- Do not rely on directory timestamps alone to distinguish semantically different artifacts.
- Do not create near-identical slugs that differ only by superficial wording when they represent the same structured output.

Examples:
- Better: `checkout-conversion-impact-map-q2-2026`
- Better: `checkout-conversion-impact-map-mobile`
- Avoid: `checkout-conversion-impact-map-2`
- Avoid when possible: `checkout-conversion-impact-map-x7f3`

## Reserved Characters and Formatting Constraints
Machine-facing names must be portable across common filesystems and tooling.

Rules for slugs and machine-facing folder names:
- use lowercase letters `a-z`
- use digits `0-9` when needed
- use hyphens `-` as the standard word separator
- avoid repeated separators
- do not use spaces
- do not use uppercase letters
- do not use slashes, backslashes, colons, semicolons, commas, quotes, question marks, asterisks, angle brackets, pipes, or hash characters
- do not use leading or trailing hyphens
- do not use leading dots for structured output names

Guidance:
- Dates should use machine-sortable forms such as `2026-04` or `2026-q2` inside slugs when needed for semantic disambiguation.
- Versions should remain in metadata unless an external format convention requires them in a deliverable filename.
- Uniqueness suffixes should be deterministic where possible.
- Keep names reasonably short without sacrificing clarity.

Acceptable separators:
- hyphen for machine-facing slugs
- double underscore in generated output and runtime filenames where field separation improves readability

## Relationship to Other Shared References
Use this file together with the other shared references, each for its own boundary.

- `project-layout.md` defines the folder scaffold.
- `artifact-location-rules.md` defines where artifacts and outputs belong.
- `workspace-contract.md` defines root resolution, bootstrap behavior, independent skill execution, and runtime expectations.
- `artifact-schema.md` defines artifact metadata fields and semantics.
- `artifact-lifecycle.md` defines versioning, supersession, compatibility, and stale-state behavior.
- `render-contract.md` defines render families, render targets, and derivative render expectations.
- `update-integrity-rules.md` defines how updates preserve unchanged content, traceability, and stable identifiers.

This file should be referenced when a question is specifically about naming, not placement, schema shape, lifecycle logic, or execution flow.

## Non-Negotiable Rules
- Machine-facing names use lowercase by default.
- Slugs use kebab-case.
- Skill slugs are stable and do not change with marketing or display wording.
- Artifact slugs are stable for the life of the artifact identity.
- structured output file names are fixed: the structured markdown output, the human-readable summary, execution notes, source traceability notes, open questions.
- Standard render file names remain fixed when present.
- Deterministic disambiguation is required when collisions would otherwise occur.
- Partial updates must not create naming drift.
- Exports and outputs must remain traceable back to the structured markdown output.
- Metadata, not ad hoc renaming, carries version, supersession, and compatibility meaning.

## Quick Compliance Checklist
- Is every machine-facing slug lowercase kebab-case?
- Does each skill path align with `skills/<skill-slug>/SKILL.md`?
- Does each artifact folder use one stable artifact slug?
- Are structured output file names unchanged?
- Are render package file names unchanged where renders exist?
- Can every output file be traced back to one structured output slug?
- Are execution records named with a sortable timestamp and skill slug?
- Are aliases clearly named and unambiguous?
- Did you keep display titles separate from slugs and IDs?
- Did you avoid random or presentation-driven naming unless unavoidable?
- Did partial updates preserve the existing canonical names?
