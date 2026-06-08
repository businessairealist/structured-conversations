# Dependency Recipes

## Purpose

This file defines how skills chain together through explicit dependency recipes.

Its goal is predictable orchestration, reduced drift, safe reuse of upstream artifacts, and clear readiness expectations between conversations and skills. A dependency recipe tells a downstream skill what it should rely on, what must already be true before handoff, and what lineage must survive the transition into the next artifact.

## Scope

This file governs dependency recipes and handoff patterns across skills and collections.

It applies to both direct one-step handoffs and longer multi-skill workflows.

It does not redefine runtime orchestration, artifact schema details, placement rules, or naming rules. Those behaviors are owned primarily by sibling shared references. This file focuses on dependency structure: what commonly depends on what, what must exist before a skill runs well, and what makes a handoff reliable and easy to explain to a user.

## Relationship to Other Shared References

This file complements the shared references that define the rest of the operating contract:

- `workspace-contract.md` defines how the workspace root is resolved, how standard folders and indexes are initialized, and how independently called skills must search for required material.
- `artifact-location-rules.md` defines where artifacts live and how standard lookup locations are interpreted.
- `artifact-schema.md` defines structured output structure, required files, and required metadata fields.
- `artifact-lifecycle.md` defines versioning, supersession, staleness, compatibility, and update-state behavior.
- `quality-gates.md` defines the actual gate criteria and pass/fail logic.
- `evidence-normalization.md` defines how raw notes, quotes, screenshots, metrics, and prior artifacts are normalized for reuse.
- `update-integrity-rules.md` defines how partial updates preserve stable content, stable identifiers, traceability, and downstream safety.

This file focuses on two narrower questions: what commonly depends on what, and what must be true for the handoff to be reliable.

## Core Concepts

**Dependency recipe**  
A dependency recipe is the handoff contract between upstream and downstream work. In user-facing language, it should feel like a clear next step, not hidden orchestration. It states the expected upstream artifact or evidence shape, any readiness conditions, any acceptable fallback inputs, and the downstream artifact that should result.

**Upstream artifact**  
An upstream artifact is the structured markdown output, normalized evidence bundle, or other approved input that a downstream skill consumes. It is the actual handoff object, not a verbal recollection of prior work.

**Downstream artifact**  
A downstream artifact is the canonical output created after a successful handoff. It must preserve lineage to the exact upstream material that informed it.

**Workflow recipe**  
A workflow recipe is a named multi-step pattern that links several dependency recipes into a larger cross-skill flow. It describes a recurring end-to-end path such as discovery to roadmap or story to example to Gherkin.

**Quality gate**  
A quality gate is a readiness check layered onto a dependency recipe. It does not define the whole workflow. It answers whether a specific handoff is safe to make.

**Supporting skill**  
A supporting skill is a helper or companion skill that improves the quality or usability of a main skill’s output, but is not automatically the required handoff target. Supporting skills influence preparation, translation, selection, or refinement.

**Runtime profile**  
A runtime profile is the execution mode for a skill. It defines how a skill behaves operationally, such as artifact builder, translator/scaffolder, selector/router, planner/decomposer, quality gate, template generator, diagnostic classifier, or hypothesis tree. A runtime profile explains *how* a skill runs, not *what* it depends on.

**Latest compatible artifact**  
The latest compatible artifact is the most recent upstream artifact that still matches the downstream skill’s dependency requirements. Compatibility is not timestamp-only selection. The artifact must be semantically usable, not stale for the intended handoff, and compatible with the downstream artifact family, gate expectations, and declared lifecycle metadata.

## General Handoff Rules

- Downstream skills should consume structured outputs or normalized evidence rather than informal summaries whenever possible.
- Downstream skills must preserve lineage to the specific upstream artifacts actually used.
- Handoffs must carry forward assumptions, open questions, unresolved ambiguity, and known compatibility concerns rather than silently discarding them.
- Downstream skills should prefer existing compatible upstream artifacts over unnecessary regeneration.
- Downstream skills should try to locate the best user-relevant existing content first and only ask for pasted or uploaded input when suitable content cannot be found safely.
- A dependency recipe is a readiness contract, not merely a suggested sequence.
- Every skill may be called independently, so every recipe must assume that the downstream skill may need to resolve required upstream material from the workspace rather than from conversational context.
- structured outputs are the source of truth. Human-readable markdown and renders help interpretation, but they do not replace canonical metadata.

## Upstream Artifact Expectation Rules

A dependency recipe must state what the downstream skill expects from upstream material in operational terms.

At minimum, the recipe should describe:

- the required artifact family or artifact type
- the required semantic completeness
- any required quality gate status
- any required lineage or traceability presence
- acceptable evidence alternatives when no prior structured output exists

Expectation definitions must be narrow enough to prevent brittle handoffs. Do not write a recipe that says the downstream skill needs “some prior work” or “relevant inputs.” State the narrowest useful requirement instead.

Use the following expectation dimensions when documenting a recipe:

- **Artifact family or type**: for example board canvas, tree, matrix, form statement, scenario executable specification, normalized evidence bundle, or raw request context.
- **Semantic completeness**: the artifact must contain the fields or decisions the downstream skill actually needs. A story consumer may need actor, goal, outcome, and acceptance framing. A Gherkin consumer may need rules and concrete examples, not just a story title.
- **Gate status**: if a gate materially affects downstream correctness, the recipe must name it explicitly.
- **Compatibility status**: the upstream artifact must not be stale or incompatible for the intended downstream use.
- **Fallback evidence**: if no canonical upstream artifact exists, the recipe may define approved alternatives such as normalized evidence or raw intake material.

Preferred upstream expectation order:

1. structured output already produced for the required purpose.
2. Normalized evidence that meets the downstream skill’s minimum semantic needs.
3. Raw request context or source evidence only when the recipe explicitly allows direct generation from raw material.

## Downstream Resolution Rules

Downstream skills should resolve upstream artifacts using the established workspace discovery order:

1. explicit path or artifact specified by the request
2. manifest aliases or pointers
3. prior run metadata
4. collection-specific standard roots
5. output catalog
6. latest compatible artifact

Dependency recipes should assume latest compatible selection, not timestamp-only selection.

Compatibility checks should include, at minimum:

- required artifact family or type
- required semantic completeness
- required gate status
- declared compatibility metadata
- stale state and recompute implications
- whether the artifact still supports the requested downstream use

When multiple plausible upstream artifacts exist, the downstream skill must not guess. It should either:

- select the single latest compatible artifact when compatibility is unambiguous, or
- stop and ask for clarification when multiple candidates are materially plausible and the recipe cannot safely choose among them

When possible, that clarification should be presented as a short user-facing choice list rather than a request for raw file paths.

Downstream resolution should prefer structured outputs already registered in the workspace and visible through run metadata. Manual path hunting should be the exception, not the norm.

## Quality Gate Integration Rules

Quality gates are readiness checks layered onto dependency recipes.

A quality gate does not replace the dependency recipe. It strengthens the handoff by verifying that a draft upstream artifact is safe for the next step.

Recipes may require a gate before handoff when readiness materially affects downstream correctness, coverage, or decomposition quality.

The established gates are:

- `story_ready_for_example_mapping`
- `example_map_ready_for_gherkin`
- `story_ready_for_subtasking`
- `roadmap_ready_for_okri_alignment`

Gate outcomes must be visible through canonical metadata or run metadata rather than informal memory. A downstream skill should be able to determine whether a required gate has already passed by inspecting registered artifacts and run outputs.

Gate integration rules:

- If a recipe names a required gate, the downstream skill must check for a passed result before continuing.
- If the gate has failed, the downstream skill should stop the handoff and route back to repair or rewrite work.
- If the gate has not been run, the downstream skill should not silently assume readiness.
- A passed gate validates readiness for a specific handoff, not for all later downstream uses.

## Canonical Workflow Recipes

### `discovery-to-roadmap`

**Purpose**  
Turn raw discovery material into structured maps, prioritized opportunities, and a roadmap artifact that can later support strategic alignment and OKRI work.

**Typical starting inputs**  
Raw request context, source documents, notes, screenshots, interviews, quotes, metrics tables, or normalized evidence.

**Typical core skill chain**  
A typical chain starts in `mapping-discovery` and may move into `strategy-experimentation`:

- empathy-oriented inputs through `empathy-map-builder`, `empathy-map-facilitator`, or `empathy-insight-extractor`
- behavior and outcome framing through `impact-map-builder`, `impact-map-facilitator`, `impact-to-story-translator`, `opportunity-solution-tree-builder`, `solution-experiment-designer`, `customer-journey-map-builder`, `journey-friction-analyzer`, `value-stream-map-builder`, or `value-stream-optimization-prioritizer`
- backlog and release structure through `user-story-map-builder`, `story-hierarchy-organizer`, or `release-slice-planner`
- roadmap formation through `goal-oriented-roadmap-builder`, `now-next-later-roadmap-scaffolder`, or related strategy skills
- optional OKRI alignment through `objective-keyresult-initiative-scaffolder`, `okr-level-cascade-builder`, or `okri-builder`

**Major handoff artifacts**  
Normalized evidence bundles, empathy maps, impact maps, opportunity-solution trees, journey maps, value stream maps, story maps, release slices, and roadmap boards.

**Major quality gates**  
`roadmap_ready_for_okri_alignment` applies when the roadmap becomes the direct upstream input for OKRI scaffolding or alignment.

**Expected final artifact families or outcomes**  
Board, tree, matrix, or text artifacts during discovery; roadmap board artifacts for planning; form statement or board artifacts when the flow continues into OKRI work.

### `pitch-to-epic-to-story`

**Purpose**  
Turn vision and narrative framing into a strategic epic and then into implementation-ready story framing.

**Typical starting inputs**  
Base product description, source pitch, future press release context, audience variants, or other vision artifacts.

**Typical core skill chain**  

- vision shaping in `vision-messaging` through `product-elevator-pitch-writer`, `product-elevator-pitch-facilitator`, `future-press-release-writer`, `future-press-release-facilitator`, `press-release-structure-selector`, `working-backwards-section-scaffolder`, or `persona-pitch-adapter`
- epic framing in `feature-specification` through `elevator-pitch-to-epic-translator`, `epic-hypothesis-statement-scaffolder`, or `outcome-driven-epic-writer`
- story framing in `story-delivery` through `user-story-format-selector` and `user-story-drafter`

**Major handoff artifacts**  
Pitch artifacts, future press release artifacts, adapted narrative matrices, epic form statements, and user story form statements.

**Major quality gates**  
`story_ready_for_example_mapping` commonly applies once the story artifact becomes the handoff target for example-oriented downstream work.

**Expected final artifact families or outcomes**  
Form statement artifacts for pitch, press release, epic, and story stages; matrix artifacts when persona adaptation is part of the workflow.

### `story-to-example-to-gherkin`

**Purpose**  
Turn a story into explicit rules, examples, questions, and executable behavioral scenarios.

**Typical starting inputs**  
A draft user story, a formatted story artifact, or a story plus known rules and examples.

**Typical core skill chain**  

- story normalization in `story-delivery` through `user-story-format-selector` or `user-story-drafter`
- feature and example clarification in `feature-specification` through `feature-map-builder`, `feature-rule-example-scaffolder`, `example-map-builder`, `example-map-facilitator`, `rule-example-question-scaffolder`, or `acceptance-criteria-scaffolder`
- scenario writing through `gherkin-scenario-writer`
- optional extension into living verification through `living-documentation-builder`

**Major handoff artifacts**  
Story form statements, feature maps, example maps, rule/example/question matrices, acceptance-criteria matrices, Gherkin scenario artifacts, and living documentation artifacts.

**Major quality gates**  

- `story_ready_for_example_mapping` before example-oriented work
- `example_map_ready_for_gherkin` before Gherkin scenario generation or living documentation extension

**Expected final artifact families or outcomes**  
Board, matrix, and scenario executable specification artifacts.

### `map-to-subtasks`

**Purpose**  
Turn mapped work and structured stories into slices, subtasks, and tactical delivery plans.

**Typical starting inputs**  
Story maps, structured activity/task/story hierarchies, release constraints, or ready stories.

**Typical core skill chain**  

- map and slice preparation in `mapping-discovery` through `user-story-map-builder`, `user-story-map-facilitator`, `story-hierarchy-organizer`, or `release-slice-planner`
- tactical decomposition in `story-delivery` through `story-splitting-method-selector`, `user-story-splitter`, `hamburger-slice-scaffolder`, `spidr-slice-generator`, `story-subtask-planner`, `sequence-diagram-subtask-scaffolder`, `code-review-to-subtask-translator`, or `subtasking-workshop-facilitator`

**Major handoff artifacts**  
Story map boards, release slice boards, split-story plan bundles, subtask flows, and subtask matrices.

**Major quality gates**  
`story_ready_for_subtasking` applies when a story becomes the direct upstream for tactical decomposition.

**Expected final artifact families or outcomes**  
Board, flow, matrix, and plan-task-bundle artifacts that organize implementation work into concrete slices and subtasks.

### `observation-to-hypothesis-to-okri`

**Purpose**  
Turn observed signals or problems into explicit hypotheses, measurable experiments, and aligned OKRI outputs.

**Typical starting inputs**  
An observation, metric problem, business signal, candidate solution, or roadmap-derived bet.

**Typical core skill chain**  

- observation framing through `observation-to-hypothesis-translator` or `data-driven-decision-framer`
- hypothesis and experiment shaping through `hypothesis-experiment-designer` and `experiment-signal-passfail-designer`
- strategic alignment through `objective-keyresult-initiative-scaffolder`, `okr-level-cascade-builder`, or `okri-builder`

**Major handoff artifacts**  
Observation trees, hypothesis trees, experiment signal matrices, OKRI boards, and final OKRI form statements.

**Major quality gates**  
No gate is required for every observation-to-hypothesis handoff. `roadmap_ready_for_okri_alignment` applies when the workflow uses a roadmap artifact as the direct strategic upstream for OKRI alignment or builder stages.

**Expected final artifact families or outcomes**  
Tree and matrix artifacts for learning design, then board or form statement artifacts for OKRI outputs.

## Cross-Collection Dependency Patterns

### Foundation routing -> mapping discovery

Foundation routing skills clarify vague inputs before heavier mapping begins. `verb-noun-rewriter` and `syntax-pattern-selector` commonly sharpen the request, normalize wording, and reduce ambiguity before evidence is mapped into empathy, impact, journey, value stream, or story structures. The typical upstream artifact is normalized request context or a lightweight text artifact. The downstream use is clearer actor, goal, and outcome framing for visual mapping.

### Mapping discovery -> vision messaging

Mapping outputs often become the evidence base for narrative packaging. Empathy maps, impact maps, journey maps, and story maps can feed product elevator pitches, future press releases, and persona-adapted narratives. The typical upstream artifact is a board or tree artifact that already captures customer problems, actor context, desired behaviors, or journey friction. The downstream use is a form statement or matrix artifact that tells a coherent story without re-deriving the underlying evidence.

### Vision messaging -> feature specification

Vision artifacts should not stop at messaging. Product pitches, future press releases, and working-backwards outputs commonly feed epic creation and feature framing. The typical upstream artifact is a pitch or press-release form statement. The downstream use is an epic or feature-specification artifact that preserves customer problem framing, promised value, and measurable outcomes.

### Feature specification -> story delivery

Feature maps, example maps, acceptance-criteria artifacts, and epic statements commonly feed story selection, story drafting, story formatting, and tactical delivery work. The typical upstream artifact is a feature-specification board, matrix, or form statement that contains rules, examples, or epic intent. The downstream use is a story artifact, split-story plan, or subtask plan.

### Story delivery -> quality diagnostics

Delivery artifacts provide the behavioral context needed for defects and diagnostics. A user story, split story, subtask plan, or Gherkin scenario gives the diagnostic skill a baseline for what should happen. The typical upstream artifact is a story or scenario artifact. The downstream use is a defect report, reproducibility scaffold, severity/priority classification, or captured diagnostic context that traces back to the failed expectation.

### Mapping discovery <-> strategy experimentation

These collections reinforce each other in both directions. Discovery artifacts surface problems, actors, and candidate behavior changes. Strategy artifacts convert those into bets, hypotheses, experiments, and OKRI alignment. Strategy outputs can then feed back into discovery to re-map opportunities, update priorities, or refine roadmap bets. The upstream artifact may be an impact map, opportunity-solution tree, journey analysis, roadmap, or hypothesis tree. The downstream use may be a roadmap board, experiment matrix, or OKRI artifact depending on the phase.

## Recipe Authoring Pattern

Future authors should document dependency recipes using a stable pattern so skills, scripts, and workflow planners can interpret them consistently.

Recommended recipe fields:

- **Recipe name**: stable workflow or handoff name.
- **Purpose**: what this recipe is for and why the handoff exists.
- **Upstream requirements**: required artifact family or type, minimum semantic completeness, required lineage, and any gate prerequisites.
- **Acceptable alternatives**: normalized evidence or raw intake allowed when the canonical upstream artifact does not yet exist.
- **Quality gate requirements**: named gates that must pass before the handoff is valid.
- **Downstream output**: expected artifact family or artifact types produced after the handoff.
- **Compatibility concerns**: stale-state rules, supersession expectations, semantic mismatch risks, and downstream recompute implications.
- **Common failure conditions**: missing upstream artifact, unresolved ambiguity, failed gate, incompatible version, or insufficient semantic completeness.

Authoring rules:

- Name the narrowest useful upstream requirement.
- Prefer artifact families and semantic requirements over vague descriptions.
- State whether normalized evidence is an approved fallback.
- Name all required gates explicitly.
- State whether multiple upstream variants are allowed or whether the recipe requires a single canonical source.
- Describe downstream output in artifact terms, not just conversational terms.
- Document failure conditions up front so orchestrators and skill authors do not improvise brittle behavior.

## Missing, Stale, or Incompatible Upstream Artifact Rules

When no suitable upstream artifact exists, the downstream skill should check whether the recipe explicitly allows fallback to normalized evidence or raw source material. If yes, it may proceed from that fallback input and should record that no canonical upstream artifact was available. If not, it should stop and request the missing artifact or the source needed to create it.

When only stale artifacts exist, the downstream skill should not treat recency alone as the issue. It should inspect why the artifact is stale and whether the stale reason affects the requested downstream use. If the stale condition breaks compatibility, the downstream skill should stop or route to recomputation. If the stale condition does not affect the requested use and the artifact remains compatible, the downstream skill may proceed but should record the decision and preserve the stale marker.

When only incompatible artifacts exist, the downstream skill should not coerce them into place. It should either transform from an approved alternative upstream artifact, regenerate the missing compatible upstream artifact, or stop and ask for clarification.

When multiple plausible candidates exist, the downstream skill must not guess. It should compare them using recipe requirements, lifecycle metadata, gate status, and compatibility metadata. If one candidate is clearly the latest compatible artifact, use it. If multiple candidates remain materially plausible, stop and ask.

When the requested recipe depends on a gate that has not been passed, the downstream skill must not proceed as though the gate were implicitly satisfied. It should either invoke the required quality-gate step, route to the repair skill, or stop.

Fallback rules:

- Fall back to normalized evidence when the recipe allows evidence-first generation and the evidence satisfies minimum semantic needs.
- Fall back to raw intake or source files only when the recipe explicitly allows direct generation from raw inputs or when no structured output exists yet and the skill is designed to build the first structured output in the chain.
- Stop and ask instead of improvising when the requested handoff would require guessing among multiple candidate upstreams, inventing missing semantics, bypassing a required gate, or overriding declared incompatibility.

## Assumption and Open-Question Carry-Forward Rules

Dependency recipes must preserve important assumptions and unresolved questions across handoffs.

The carry-forward contract is simple:

- upstream assumptions remain visible unless explicitly resolved
- open questions remain visible unless explicitly answered
- unresolved ambiguity remains attached to lineage rather than being silently erased
- downstream refinement may narrow, answer, or supersede uncertainty, but must not pretend the uncertainty never existed

Carry-forward requirements:

- Preserve assumptions and open questions in canonical metadata and companion files such as open questions.
- Preserve lineage to the exact upstream artifacts that introduced or influenced the uncertainty.
- When a downstream skill resolves an upstream question, record the resolution in the new artifact and keep traceability to the earlier unresolved state.
- When a downstream skill cannot resolve the inherited uncertainty, restate it in downstream form rather than dropping it.
- When a downstream skill sharpens scope or restructures content, retain the inherited assumptions that still matter to downstream interpretation or validation.

A good recipe makes inherited uncertainty easy to inspect before downstream execution begins.

## Relationship to Other Shared References

Use the sibling shared references as follows:

- For runtime resolution behavior, use `workspace-contract.md` and `project-layout.md`.
- For artifact placement and lookup behavior, use `artifact-location-rules.md`.
- For canonical schema fields and required files, use `artifact-schema.md`.
- For lifecycle, supersession, stale-state, and compatibility behavior, use `artifact-lifecycle.md`.
- For gate definitions and pass/fail criteria, use `quality-gates.md`.
- For evidence reuse and normalization behavior, use `evidence-normalization.md`.
- For partial-update and regeneration safety, use `update-integrity-rules.md`.

This file should be used when the question is, “What should this skill depend on, and what must be true before the handoff is safe?”

## Non-Negotiable Rules

- Every dependency recipe must state explicit upstream expectations.
- Downstream resolution must prefer the latest compatible artifact, not merely the newest artifact.
- Downstream skills must not silently guess across ambiguous upstream candidates.
- Required quality gates must be enforced when named by the recipe.
- Lineage to the specific upstream artifacts used must be preserved.
- Assumptions, open questions, and unresolved ambiguity must be carried forward or explicitly resolved.
- structured outputs remain the source of truth.
- Normalized evidence may replace a missing canonical upstream artifact only when the recipe explicitly allows that fallback.
- Stale or incompatible upstream artifacts must not be treated as valid by default.
- Every independently called skill must search standard project locations before asking for missing paths.
- User-facing retrieval should prefer titles, topics, statuses, and recency over raw nested folder paths.

## Quick Compliance Checklist

- [ ] The recipe names the upstream artifact family or artifact type.
- [ ] The recipe states the minimum semantic completeness required.
- [ ] The recipe states any required quality gate.
- [ ] The recipe states acceptable fallback inputs, if any.
- [ ] The recipe aligns upstream resolution with workspace discovery order.
- [ ] The recipe uses latest compatible selection, not timestamp-only selection.
- [ ] The recipe explains what happens when upstream material is missing, stale, incompatible, or ambiguous.
- [ ] The recipe preserves lineage, assumptions, and open questions.
- [ ] The recipe identifies the expected downstream artifact family or outcome.
- [ ] The recipe does not rely on informal memory or undocumented handoffs.
