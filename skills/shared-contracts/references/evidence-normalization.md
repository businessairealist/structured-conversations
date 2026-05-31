# Evidence Normalization

## Purpose
This file defines how raw source material is normalized into reusable intermediate evidence.

The goal is consistency, traceability, reuse, and reduced duplication of intake logic across skills. Normalized evidence gives downstream skills a stable evidence surface without severing the connection to original source material.

## Scope
This file governs normalization of source material into reusable evidence.

It applies across collections and artifact families. It covers evidence derived from notes, interviews, screenshots, diagrams, metrics, tables, and prior generated artifacts.

This file does not replace `artifact-schema.md`, `workspace-contract.md`, or `artifact-location-rules.md`. Those files still own structured output schema, runtime/workspace behavior, and broad placement rules.

## Relationship to Other Shared References
`workspace-contract.md` defines how workspace roots are resolved, how standard folders are used, and how artifacts are managed. This file defines what normalized evidence must preserve so that evidence can be safely created and consumed within that workspace model.

`project-layout.md` defines the shared scaffold and standard directories. This file only defines how normalized evidence should be treated within that scaffold.

`artifact-location-rules.md` defines general placement expectations for artifacts. This file narrows that down for normalized evidence and fixes its shared storage location.

`artifact-schema.md` defines structured output structure. This file does not replace that schema. It defines the minimum evidence components that must be present even when exact field names are implemented elsewhere.

`artifact-lifecycle.md` defines versioning, compatibility, staleness, and supersession rules. This file explains when normalized evidence should be reused, refreshed, versioned, or reconsidered for downstream compatibility.

`update-integrity-rules.md` defines how updates must remain auditable and scope-bounded. This file applies those expectations specifically to normalized evidence so source lineage and interpretation boundaries remain intact.

This file focuses on transforming source material into trustworthy intermediate evidence for downstream use.

## Evidence Classes
- **Raw source inputs**: Original materials such as source documents, images, notes, data files, and upstream artifacts. These remain the source of truth for what was originally said, shown, measured, or recorded.
- **Normalized evidence**: Reusable, structured intermediate evidence extracted from raw inputs or upstream artifacts. This is not the final semantic authority. It exists to make downstream reuse safer and more consistent.
- **structured outputs**: Generated output packages produced by skills. These are the source of truth for generated outputs, with canonical content governed by the artifact contract rather than by normalized evidence.
- **Rendered/presentation outputs**: Derivative renderings, exports, previews, or presentation-ready outputs. These are not the source of truth for meaning.
- **Project-specific references**: Contextual reference materials stored for the project. These may inform work, but they are not automatically normalized evidence unless explicitly extracted and normalized as evidence.

Raw source inputs are authoritative for original material. structured outputs are authoritative for generated artifact content. Normalized evidence is intermediate and traceable. Rendered outputs are derivative.

## Source Material vs Normalized Evidence
Raw inputs are original source documents, images, notes, data files, or prior artifacts.

Normalized evidence is a reusable, structured intermediate representation extracted from those sources. Its job is to preserve meaning while making the material easier to reuse across skills.

Normalization is not permission to rewrite source intent, flatten important context, or invent evidence that the source does not support.

Normalization may reorganize, label, segment, and structure evidence. It must not silently change what the source materially means.

## Supported Evidence Types
The shared evidence ingestion contract supports these evidence types:

- **Notes**: Normalize freeform notes into reusable evidence that preserves entities, actions, problems, goals, decisions, assumptions, quotes, and open questions.
- **Interview snippets and quotes**: Normalize interview material into attributed snippets, quotes, observations, and themes without losing speaker or context boundaries.
- **Screenshots and diagrams**: Normalize image-based sources into visible text, structural elements, observed relationships, and explicitly labeled interpretation.
- **Metrics tables**: Normalize structured data into reusable metric evidence that preserves metric names, values, units, scope, segmentation, and source context.
- **Prior generated artifacts**: Normalize prior artifacts into reusable extracts or evidence views while preserving artifact lineage and the semantic authority of the original output package.

## When Normalization Is Required
Normalization is required when a skill depends on research notes, interviews, screenshots, diagrams, metrics, tables, or multi-source evidence synthesis.

Normalization is also required when downstream work depends on consistent separation between quote, observation, fact, inference, and open question.

Normalization is strongly recommended when multiple downstream skills may reuse the same source material.

Normalization is strongly recommended for workflows that repeatedly transform evidence into downstream maps, specifications, diagnostics, hypotheses, and strategy artifacts. In the hardened inventory, shared evidence ingestion is explicitly defined around notes, interview snippets and quotes, screenshots and diagrams, metrics tables, and prior generated artifacts, with normalized evidence stored under the working directory. fileciteturn1file10

Direct source use without separate normalization is acceptable only when all of the following are true:
- the input is simple and unambiguous
- the source will likely be used once
- the downstream task does not require evidence-layer separation
- direct use does not increase the risk of losing traceability or misreading the source

Even when separate normalization is skipped, the skill must still preserve clear source references.

## Normalized Evidence Storage Rules
Normalized evidence belongs under:

the working directory

That path is the shared normalized evidence location established by the hardened report and inventory. fileciteturn1file10turn1file11

Normalized evidence should live in canonical, reusable folders or files governed by the same workspace discipline used for other shared artifacts.

Normalized evidence does not replace original materials stored in `intake/` or `inputs/`. Original inputs must remain available and traceable.

Normalized evidence must not be stored only as ad hoc notes inside downstream artifacts when the intent is shared reuse. Shared reusable evidence belongs in the shared normalized evidence location, then downstream artifacts may reference it.

Exact naming, indexing, and broader placement behavior are governed by the shared project layout and artifact location references.

## Core Normalization Principles
The following are contract rules, not suggestions:

- Preserve source meaning.
- Preserve source boundaries.
- Separate observation from inference.
- Preserve traceability to original source locations.
- Prefer reusable structure over one-off prose notes.
- Avoid lossy summarization when downstream fidelity matters.
- Do not silently collapse uncertainty into false certainty.
- Do not silently merge multiple speakers, contexts, or sources into one voice.
- Keep normalization deterministic enough that downstream skills can reuse it consistently.
- Preserve per-source attribution in multi-source normalization.
- Do not allow normalized evidence to override the semantic authority of original source inputs or structured outputs.

## Minimum Normalized Evidence Structure
This file does not define the full canonical schema. It does define the minimum evidence components that normalized evidence must carry in some implemented form.

Each normalized evidence record should include:

- **Evidence identifier**: A stable identifier for the normalized evidence record or evidence item.
- **Evidence type**: The supported evidence type or subtype being normalized.
- **Source reference or references**: The original file, image, note, dataset, artifact, or observation source used to produce the normalized evidence.
- **Source locator**: A way to trace the evidence back to a meaningful location such as page, paragraph, section, timestamp, cell range, panel, region, node, or artifact section.
- **Normalization timestamp**: When the evidence was extracted or normalized.
- **Normalized content**: The reusable structured content produced from the source.
- **Confidence or certainty indicator when relevant**: Required when the evidence includes extraction uncertainty, interpretation, or incomplete source visibility.
- **Assumptions**: Any assumptions made during normalization.
- **Unresolved questions**: Any ambiguity or missing information that remains open.
- **Traceability/provenance link**: Enough information for a downstream skill to understand what source material supports the normalized statement.

If a skill cannot preserve these minimum components, it has not produced reusable normalized evidence.

## Quote, Observation, Fact, Inference, and Question Separation Rules
Normalized evidence must clearly separate these layers:

- **Verbatim quote**: Exact quoted wording from a source. Quotes must remain clearly attributable to the source context and must not be rewritten as if they were direct quotes.
- **Observation**: What is directly visible, stated, measured, or otherwise present in the source without added interpretation.
- **Extracted fact**: A normalized factual statement grounded in source material and bounded by the source context.
- **Inference/theme/interpretation**: A conclusion, pattern, synthesis, or thematic reading derived from one or more observations or facts.
- **Unresolved question/ambiguity**: Anything still unclear, missing, conflicting, or unsafe to resolve automatically.

Downstream skills must be able to tell which layer they are consuming.

Inferences must not be mislabeled as facts.

Quotes must not be mislabeled as paraphrases, and paraphrases must not be mislabeled as quotes.

Every inference should point to supporting observations, facts, or quotes. If that support is missing, the inference should not be treated as reliable normalized evidence.

## Text and Notes Normalization Rules
Freeform notes, interview notes, workshop notes, written observations, and similar text sources should be normalized into structured evidence that preserves who said what, what happened, and what remains unclear.

At minimum, text and notes normalization should preserve:
- key entities
- actions
- problems or pain points
- goals or desired outcomes
- decisions if explicitly recorded
- direct quotes when present
- assumptions when present
- unresolved ambiguity

Do not flatten multiple speakers or contexts into a single untraceable voice.

If speaker attribution is known, preserve it. If attribution is uncertain, label that uncertainty explicitly.

If notes combine verbatim quotes and paraphrase, keep those layers separate.

If chronology matters, preserve sequence. If topical grouping matters more than sequence, preserve topical grouping without destroying source traceability.

Normalized notes should be structured so later mapping, synthesis, transformation, and diagnostic skills can reuse them without re-reading the entire raw note set.

## Screenshot and Diagram Normalization Rules
Screenshots, visual boards, diagrams, and image-based source material should be normalized into evidence that separates what is visibly present from what is interpreted.

Image-derived normalized evidence should distinguish:
- **Visible text extracted or transcribed**
- **Visible structural elements** such as nodes, cards, lanes, panels, connectors, columns, legends, or labeled areas
- **Observed layout or relationships** that are directly supported by the visible arrangement
- **Interpretation or story** derived from that visible content

Image-derived evidence must not infer unsupported meaning.

If text is unreadable, partially occluded, cropped, or ambiguous, record that limitation instead of guessing.

When relevant, traceability should include region, panel, frame, or conceptual area references so downstream users know where in the image the evidence came from.

Color, spacing, grouping, or iconography should only be treated as semantically meaningful when the source itself makes that meaning clear or the relationship is directly observable.

## Metrics and Table Normalization Rules
Metrics tables and structured data evidence should be normalized in a way that preserves analytical meaning and prevents accidental distortion.

At minimum, metrics normalization should preserve:
- metric names
- values
- units
- time scope or reporting window
- segmentation or cohort context
- source origin
- metric definitions or formulas when available
- missing-value or incomplete-data indicators when relevant

Headers, row meanings, column meanings, and table structure must remain recoverable.

Derived calculations such as changes, deltas, rankings, rollups, or trends must be labeled as derived values rather than as raw source values.

Normalization must not silently convert raw metrics into conclusions. Any conclusion or recommendation belongs in the inference layer.

Normalized metrics evidence should support downstream roadmap, hypothesis, prioritization, and diagnostic skills without forcing those skills to reverse-engineer basic metric context.

## Prior Artifact Normalization Rules
Prior generated artifacts may be normalized for downstream reuse when a later skill needs a reusable evidence view, extract, or subset of a prior artifact.

Normalization of prior artifacts must preserve canonical lineage. It must not sever the connection to the original output package.

If a prior artifact is already sufficiently structured, normalization may be lightweight. A reusable extract, evidence index, or evidence bundle may be enough. Full reinterpretation is not required when it adds no value.

When normalizing prior artifacts, preserve at least:
- source artifact identifier
- artifact type
- artifact version when available
- collection or artifact family context
- relevant section or field locators
- open questions or assumptions that materially affect interpretation

Normalized evidence derived from a prior artifact must not override that artifact’s semantic authority. When a conflict appears, the structured markdown output remains authoritative until intentionally superseded under the lifecycle rules.

## Traceability and Provenance Rules
Every normalized evidence record must remain traceable back to original source inputs or upstream structured outputs.

A downstream skill should be able to inspect a normalized statement and understand what source material supports it.

Multi-source normalization must preserve per-source traceability. It must not blend several sources into an untraceable synthesis.

Traceability should identify both the source object and the source location. Examples include file path, artifact identifier, page number, paragraph, note section, timestamp, row/column range, image region, panel, card, or node.

If the source is an observation recorded by a person rather than a file, preserve the observer, time, and context if available.

If one normalized statement depends on several sources, the statement should keep those links explicit rather than hiding them in a generic “combined evidence” label.

## Reuse and Refresh Rules
A skill should reuse existing normalized evidence when all of the following are true:
- it is based on the same source material
- it is still valid for the current task
- it has not been invalidated by important upstream changes
- it contains the evidence layers and granularity needed for the current task
- it remains compatible with the current downstream use

A skill should refresh or regenerate normalized evidence when any of the following are true:
- source inputs changed materially
- relevant upstream artifacts changed materially
- the existing normalization omitted evidence needed for the current task
- the prior normalization is stale, incomplete, incompatible, or too lossy
- previously unresolved ambiguity has now been resolved and that resolution matters downstream
- the current task requires stricter evidence separation or higher fidelity than the old normalization provides

Reuse is preferred over redundant regeneration when safe.

Refresh should be targeted when possible. Unchanged evidence should remain stable and traceable rather than being needlessly regenerated.

## Update Integrity Rules for Normalized Evidence
Updates to normalized evidence must preserve source lineage.

Updates must distinguish newly added interpretation from previously normalized content.

Normalization updates must not silently rewrite unrelated evidence.

When normalization materially changes meaning, downstream compatibility should be reconsidered. Existing consumers may need review, refresh, or staleness handling under the shared lifecycle rules.

Patch and change recording must remain auditable and consistent with shared update-integrity and lifecycle expectations. At minimum, updates should make it clear:
- what change was requested
- what evidence items changed
- what evidence items were preserved
- whether source references changed
- whether compatibility impact was introduced

If an update would effectively replace the prior meaning rather than revise it within scope, create a new version rather than pretending the old and new evidence are equivalent.

## Clarification and Failure Rules
A skill should stop and ask for clarification when any of the following are true:
- source material is missing, incomplete, or ambiguously referenced
- speaker or source attribution is unclear and attribution matters
- multiple interpretations are equally plausible
- image or diagram evidence lacks enough context for safe interpretation
- metric definitions, units, segmentation, or time scope are unclear
- prior artifact reuse would risk misinterpretation
- the requested normalization would require inventing missing context

A skill may proceed automatically when the source is sufficiently clear, attribution is adequate, evidence-layer separation can be preserved, and the remaining uncertainty is minor and explicitly labeled.

A skill must refuse to guess when proceeding would risk fabricating evidence, distorting source meaning, or presenting unsupported interpretation as fact.

## Non-Negotiable Rules
- Store shared normalized evidence under the working directory.
- Do not replace original source material in `intake/` or `inputs/`.
- Preserve traceability to original sources and meaningful source locations.
- Keep quote, observation, fact, inference, and question as separate evidence layers.
- Do not silently invent evidence.
- Do not silently turn uncertainty into certainty.
- Do not let normalized evidence override original source inputs or structured outputs.
- Reuse valid normalized evidence when safe.
- Refresh stale, incomplete, or incompatible normalized evidence before downstream use.
- Keep updates auditable and scope-bounded.

## Quick Compliance Checklist
- [ ] Evidence is derived from clearly identified source material.
- [ ] The normalized evidence lives under the working directory when intended for shared reuse.
- [ ] Original source material remains available in its original location.
- [ ] Each evidence item has a stable identifier or equivalent record handle.
- [ ] Each evidence item preserves source references and source locators.
- [ ] Quotes, observations, facts, inferences, and unresolved questions are clearly separated.
- [ ] Multiple speakers or sources are not flattened into one untraceable voice.
- [ ] Metrics keep names, values, units, scope, and segmentation context.
- [ ] Image-derived evidence separates visible content from interpretation.
- [ ] Prior artifact normalization preserves canonical lineage.
- [ ] Confidence, assumptions, and unresolved questions are recorded when relevant.
- [ ] Existing normalized evidence was reused when safe, or refreshed for a documented reason.
- [ ] Updates preserve lineage, avoid unrelated rewrites, and remain auditable.
