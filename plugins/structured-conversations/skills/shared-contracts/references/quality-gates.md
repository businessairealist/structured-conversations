# Quality Gates

## Purpose

This file defines the canonical quality-gate system for readiness checks between skills in this plugin.

The goal of the quality-gate system is to make handoffs safer, reduce downstream drift, and replace implicit readiness assumptions with explicit readiness decisions.

A quality gate answers one practical question: is a specific upstream artifact ready enough for a specific downstream use right now?

## Scope

This file governs gate meaning, gate outcomes, and how readiness should be interpreted across the plugin.

It applies across collections. The currently shared gates established by the hardened report and hardened inventory are:

- `story_ready_for_example_mapping`
- `example_map_ready_for_gherkin`
- `story_ready_for_subtasking`
- `roadmap_ready_for_okri_alignment`

This file does not replace `dependency-recipes.md`, `artifact-schema.md`, or `workspace-contract.md`.

This file also does not redefine project layout, artifact lookup rules, or the full artifact schema. It defines how readiness is evaluated once the latest compatible upstream artifact has been selected for evaluation.

## Relationship to Other Shared References

`dependency-recipes.md` defines which upstream artifacts, supporting references, and execution patterns are typically needed to move from one artifact or workflow step to another. This file defines whether the selected upstream artifact is actually ready for that move.

`workspace-contract.md` defines how workspace roots, standard folders, artifact indexes, and execution records are resolved and maintained. This file does not redefine those mechanics. It assumes they already exist and uses them as the surface through which gate results remain visible and traceable.

`artifact-schema.md` defines structured output structure and required fields. This file does not redefine artifact structure. It defines readiness interpretation against that structure for downstream use.

`artifact-lifecycle.md` defines versioning, supersession, compatibility, and stale-state interpretation. This file uses those lifecycle signals when deciding whether a gate may pass, conditionally pass, or fail.

`update-integrity-rules.md` defines how partial updates must preserve canonical truth, stable identifiers, and compatibility signals. This file uses those integrity outcomes when evaluating whether an updated artifact is still ready downstream.

`evidence-normalization.md` defines how raw notes, quotes, screenshots, metrics, and prior artifacts are normalized into usable evidence. This file does not normalize evidence. It decides whether an artifact built from that evidence is ready for the next step.

This file focuses on one boundary only: deciding whether a selected artifact is ready for the next downstream step.

## Core Concepts

**Quality gate**  
A quality gate is a readiness check for a specific downstream use. It is not a generic quality score and it is not a claim that an artifact is perfect.

**Dependency recipe**  
A dependency recipe describes what a skill typically needs in order to run well: likely upstream artifacts, supporting references, scripts, and workflow relationships. A dependency recipe describes expected inputs and orchestration shape. It does not decide readiness on its own.

**Validator**  
A validator checks whether something satisfies a defined rule set, format, or constraint. Examples include schema checks, input checks, and integrity checks. A validator may feed evidence into a quality gate, but a validator is narrower than a quality gate. A validator can tell you that a field is missing or malformed. A quality gate decides whether the artifact is ready for the next downstream use.

**Runtime profile**  
A runtime profile defines how a skill executes at a high level, including setup expectations, input requirements, output behavior, and workspace behavior. A runtime profile describes execution mode. It does not decide whether a specific upstream artifact is ready for a specific downstream step.

**Gate subject**  
The gate subject is the artifact, or tightly defined artifact bundle, being evaluated. The subject must be explicit. A gate must not evaluate a vague idea of “the story” or “the roadmap” without identifying the actual artifact version or update state.

**Pass / conditional pass / fail**  
These are the only standard shared outcomes.
- Pass means the artifact is ready for the named downstream use without additional blocking work.
- Conditional pass means the artifact is usable for the named downstream use, but known caveats, limits, or inherited uncertainty must be carried forward explicitly.
- Fail means readiness is not established for the named downstream use.

**Remediation**  
Remediation is the concrete next work needed after a failed or conditional outcome. Remediation must name what to refine, clarify, split, resolve, or regenerate. It must not stop at “needs work.”

**Downstream readiness**  
Downstream readiness means the artifact contains enough structure, specificity, compatibility, and bounded uncertainty for the next skill to operate without inventing core meaning.

**Latest compatible artifact**  
The latest compatible artifact is the newest artifact version that is still valid for the target downstream use according to lifecycle and compatibility signals. Gate evaluation should run against the latest compatible artifact, not merely the most recent artifact.

**Stale artifact**  
A stale artifact is an artifact whose upstream dependencies, assumptions, or compatibility signals no longer support clean downstream use. A stale artifact may still be historically valid, but it is not cleanly ready for the target next step.

**Incompatible artifact**  
An incompatible artifact is an artifact that does not match the downstream use because of artifact type, schema expectations, lifecycle signals, declared compatibility limits, or changed upstream context.

**Open question**  
An open question is a known unresolved item recorded on or alongside the artifact. Some open questions are non-blocking. Others block a clean pass because they prevent reliable downstream execution.

## General Gate Model

Every quality gate should use the same conceptual structure:

- **Gate name**: the stable gate identifier.
- **Purpose**: the downstream decision the gate is meant to support.
- **Gate subject**: the exact artifact or artifact bundle being evaluated.
- **Required inputs**: the artifact, supporting artifacts, evidence, or metadata needed to evaluate the gate.
- **Evaluation criteria**: the visible checks used to determine readiness.
- **Outcome states**: `pass`, `conditional pass`, or `fail`.
- **Remediation guidance**: the most likely next actions when the subject is not ready.
- **Recording expectations**: how the result remains visible and traceable.

A gate evaluates readiness for a particular downstream use. It does not certify universal correctness, completeness, or long-term validity.

A gate may rely on structured output content, supporting metadata, lifecycle state, open questions, and run metadata. It must not rely on hidden evaluator assumptions.

## Gate Outcome Rules

### `pass`

Use `pass` when the gate subject is ready for the named downstream use and no known blocking ambiguity, stale-state problem, or compatibility issue remains.

Operational meaning:
- downstream execution may proceed normally
- no blocking remediation is required before the named next step
- non-blocking caveats may still exist, but they do not materially change the next step

### `conditional pass`

Use `conditional pass` only when the remaining risk is explicit, bounded, and acceptable for the named downstream use.

Operational meaning:
- downstream execution may proceed only with carried-forward caveats
- unresolved items must be recorded explicitly
- the next skill must be able to operate without inventing core meaning
- a follow-up refinement, clarification, or later gate may still be required

`conditional pass` is not a shortcut for “probably okay.” It is appropriate only when the uncertainty is known, visible, and contained.

### `fail`

Use `fail` when readiness is not established for the named downstream use.

Operational meaning:
- downstream execution must not proceed as if readiness were established
- the evaluator must route to remediation, refinement, re-selection, or clarification
- the failed result must remain visible so later steps do not silently override it

## Gate Result Recording Rules

Gate results must be visible through canonical metadata or run metadata.

At minimum, each recorded gate result must identify:

- gate name
- evaluated artifact
- timestamp
- outcome
- criteria summary
- unresolved issues or remediation items

The recorded result must remain traceable to the exact artifact version or update state that was evaluated.

The recording surface may vary by implementation, but the result must remain discoverable through canonical metadata, run metadata, or both. This file does not redefine exact storage fields or file ownership. That belongs to the schema, lifecycle, and workspace references. The minimum requirement is that downstream skills and scripts can determine what was evaluated, against which artifact state, with what outcome, and why.

When a gate returns `conditional pass` or `fail`, the record should also make clear:
- which criteria did not fully pass
- which caveats must be carried forward
- which remediation actions are expected next

When a gate result is later superseded by a newer evaluation, the newer result should not erase the historical record of the earlier evaluation. The active result should point to the artifact state it applies to.

## Shared Gate: `story_ready_for_example_mapping`

**Purpose**  
Determine whether a story is specific and grounded enough to benefit from example mapping rather than collapsing into vague discussion.

**Likely gate subject**  
A user story or closely related story artifact selected as the latest compatible artifact for example-mapping work.

**Required inputs**
- the selected story artifact
- any immediate supporting context already linked to that story
- lifecycle and compatibility signals for the selected artifact
- visible assumptions and open questions, if present

**Pass criteria**
- the story has a clear actor, context, or user frame
- the story has a clear user goal, intended behavior, or clear value direction
- the story scope is defined enough to discuss rules and examples
- the story meaning is concrete enough that example mapping will clarify behavior rather than invent the story itself
- no stale or incompatible state blocks use of the story for example mapping

**Conditional-pass conditions**
- the story is generally clear, but one or two bounded questions remain about secondary details
- the story has enough meaning to map rules and examples, but a small amount of context must be carried into the session explicitly
- the story is usable for example mapping only if the unresolved items are recorded as explicit questions during the mapping step

**Fail criteria**
- the story is abstract, buzzword-heavy, or feature-slogan-like
- the user, context, or value is unclear
- the core story meaning is still unresolved
- scope is so unclear that rules and examples would be speculative
- the selected story artifact is stale or incompatible for the target use

**Common remediation actions**
- route through `verb-noun-rewriter`
- route through `syntax-pattern-selector`
- refine or redraft the story
- clarify user, value, and scope before example mapping
- re-select the latest compatible story artifact if the current one is stale or incompatible

## Shared Gate: `example_map_ready_for_gherkin`

**Purpose**  
Determine whether an example map is precise enough to become executable or near-executable Gherkin scenarios.

**Likely gate subject**  
An example map, rule/example/question artifact, or equivalent mapping artifact selected as the latest compatible artifact for scenario writing.

**Required inputs**
- the selected example map artifact
- linked story context where needed
- lifecycle and compatibility signals
- visible open questions and assumptions
- any supporting acceptance logic already attached to the map

**Pass criteria**
- rules are clear and materially usable
- concrete examples are tied to those rules
- examples are specific enough to write observable Given/When/Then behavior without invention
- unresolved questions are limited and non-blocking for the target scenario-writing step
- rule/example coverage is coherent enough that scenario writing will clarify behavior instead of guessing at it
- no stale or incompatible state blocks scenario generation

**Conditional-pass conditions**
- the map is strong enough to generate a first bounded scenario set, but some non-core examples still need expansion
- one or more questions remain, but they do not block the specific scenarios planned next
- downstream scenario writing can proceed if the caveats are recorded and the unresolved items are preserved for follow-up

**Fail criteria**
- examples are too vague, too sparse, or detached from the rules
- major rule/example mismatch exists
- unresolved ambiguity is still central to the behavior
- the evaluator would need to invent key Given, When, or Then meaning
- the selected example map artifact is stale or incompatible for Gherkin work

**Common remediation actions**
- expand examples
- clarify or tighten rules
- resolve blocking questions
- strengthen acceptance logic before scenario writing
- regenerate or update the example map before attempting Gherkin output

## Shared Gate: `story_ready_for_subtasking`

**Purpose**  
Determine whether a story is sufficiently de-risked and specified to break into actionable team work.

**Likely gate subject**  
A story plus supporting acceptance, example, or comparable specification detail selected as the latest compatible upstream set for subtasking.

**Required inputs**
- the selected story artifact
- supporting acceptance logic, example mapping, or equivalent specification detail
- lifecycle and compatibility signals
- visible assumptions, open questions, and known unknowns

**Pass criteria**
- story scope is reasonably bounded
- major unknowns are already handled, resolved, or surfaced clearly enough to plan around
- enough acceptance logic exists to identify real work
- the story is not still too large, too risky, or too ambiguous for actionable decomposition
- the story can be decomposed into work without the team inventing core behavior
- no stale or incompatible state blocks subtasking

**Conditional-pass conditions**
- the story is actionable, but one or two bounded risks still need explicit handling during planning
- most acceptance logic exists, but a small amount of supporting detail must be carried forward as a caveat
- the team can proceed with guarded subtasking because the unresolved items do not prevent identifying concrete work slices

**Fail criteria**
- the story still needs splitting
- hidden uncertainty suggests a spike is needed first
- acceptance or example detail is missing where subtasking would depend on it
- the story remains too large, too risky, or too ambiguous to assign actionable work safely
- the selected artifact set is stale or incompatible for decomposition

**Common remediation actions**
- split the story
- run a spike
- improve example mapping first
- strengthen acceptance criteria before decomposition
- re-evaluate after the latest compatible supporting artifact is available

## Shared Gate: `roadmap_ready_for_okri_alignment`

**Purpose**  
Determine whether a roadmap is outcome-grounded enough to align into OKRs or OKRIs without turning into feature theater.

**Likely gate subject**  
A goal-oriented roadmap, now-next-later artifact, or similar strategy artifact selected as the latest compatible artifact for OKR or OKRI alignment work.

**Required inputs**
- the selected roadmap artifact
- any linked strategic context that explains desired customer or business change
- lifecycle and compatibility signals
- visible assumptions, open questions, and measurement direction

**Pass criteria**
- the roadmap expresses explicit outcomes or customer or business changes
- enough initiative-to-outcome logic exists to support alignment work
- the roadmap is not merely a feature timeline
- measurable direction exists that can support key results
- the roadmap gives downstream OKR or OKRI work a usable basis for objective, key-result, and initiative alignment
- no stale or incompatible state blocks strategic alignment

**Conditional-pass conditions**
- the roadmap is outcome-led, but one part of the measurement direction still needs tightening
- some initiative-to-outcome links are weaker than desired, but the overall roadmap is usable if those caveats are carried forward
- the next OKR or OKRI step can proceed for drafting purposes while explicitly recording what still needs refinement

**Fail criteria**
- the roadmap is feature-first and outcome-light
- linkage between initiatives and desired outcomes is unclear
- no usable measurement direction exists
- the roadmap behaves like a delivery timeline rather than an outcome-guiding strategy artifact
- the selected roadmap artifact is stale or incompatible for OKR or OKRI alignment

**Common remediation actions**
- strengthen outcome framing
- clarify customer-needs-to-outcome links
- clarify initiative-to-outcome logic
- add measurable direction that can support key results
- refine the roadmap before OKRI work

## Conditional Pass and Escalation Rules

A conditional pass is appropriate only when all of the following are true:

- the gate subject is still usable for the named next step
- the remaining uncertainty is explicit rather than hidden
- the remaining uncertainty is bounded rather than structural
- the unresolved items do not require the downstream skill to invent core meaning
- the next step can carry the caveats forward safely

A conditional pass must record:
- the explicit unresolved items
- why those items are not blocking for the named next step
- what follow-up work is required
- whether a later re-gate, refinement step, or clarification checkpoint is required

A conditional pass is not a substitute for deciding. If the evaluator cannot explain why the next step is still acceptable, the result should be `fail`, not `conditional pass`.

A conditional pass should escalate to a required follow-up gate or refinement step when:
- the unresolved issue will become blocking at the next downstream boundary
- the missing detail is acceptable for drafting but not for execution
- downstream work will create a new structured output that should not be treated as assumption-free
- the artifact is usable temporarily but should not be relied on as a stable readiness signal beyond the immediate next step

## Stale, Incompatible, or Ambiguous Upstream Rules

Latest-compatible selection and lifecycle interpretation must happen before or during gate evaluation.

A gate must not grant a clean pass to an artifact that is stale for the target downstream use.

A gate must not grant a clean pass to an artifact that is incompatible for the target downstream use.

If the selected artifact is stale:
- the evaluator should interpret lifecycle signals first
- the evaluator may fail immediately when stale-state is clearly blocking
- the evaluator may issue only a conditional pass if the stale condition is explicitly bounded and still acceptable for the immediate next step
- the stale reason must remain visible in the recorded result

If the selected artifact is incompatible:
- the evaluator should fail the gate
- the next action should be to select a compatible artifact, regenerate the artifact, or update the upstream artifact into a compatible state

If artifact selection is ambiguous:
- the evaluator must not guess silently
- the evaluator should resolve the latest compatible artifact using the canonical registry, lifecycle metadata, and declared compatibility signals
- if multiple candidates remain materially ambiguous after normal resolution, the evaluator must stop and ask rather than inventing a selection basis

## Assumption and Open-Question Handling Rules

Gates must consider assumptions and open questions. They must not ignore them just because the main artifact body looks complete.

Not all open questions are blocking. A non-blocking open question may still allow `pass` or `conditional pass` when it does not affect the named downstream use materially.

Blocking open questions must prevent a clean pass.

A gate should treat an assumption or open question as blocking when it affects:
- core artifact meaning
- core behavioral interpretation
- scope boundaries
- compatibility for the target next step
- measurement direction needed by the next step
- downstream execution in a way that would force invention

Conditional passes must make inherited uncertainty visible to downstream steps.

Downstream skills must not silently treat gate-passed artifacts as assumption-free. A passed artifact is ready for a named next use. It is not a claim that all assumptions have been eliminated.

## Downstream Behavior Rules

Downstream skills must treat gate outcomes as operational inputs, not just commentary.

For `pass`:
- normal downstream execution may proceed
- the downstream skill may rely on the artifact for the named use
- the downstream skill should still preserve traceability to the evaluated artifact state when relevant

For `conditional pass`:
- guarded downstream execution may proceed
- the downstream skill must carry forward the caveats, unresolved items, or follow-up requirements
- the downstream skill must not suppress or overwrite inherited uncertainty
- where relevant, the downstream skill should record that it relied on a conditional gate outcome

For `fail`:
- downstream execution should route to remediation or refinement rather than silent continuation
- the downstream skill must not behave as though readiness were established
- if an alternate latest compatible artifact exists, the flow may re-run selection and evaluate that artifact instead
- if no acceptable artifact exists, the flow should stop at remediation or clarification

When relevant, downstream skills should record the gate result they relied on so later readers can tell which readiness decision supported the downstream artifact.

## Gate Authoring Pattern

Future gate authors should document additional gates using the following pattern:

**Gate name**  
Stable identifier for the readiness check.

**Purpose**  
What downstream decision this gate is meant to support.

**Gate subject**  
The exact artifact or artifact bundle being evaluated.

**Required inputs**
- structured output(s)
- supporting artifact(s), if any
- lifecycle and compatibility signals
- visible assumptions and open questions
- any downstream-specific context needed for evaluation

**Pass criteria**
- explicit conditions that establish readiness for the named downstream use

**Conditional-pass conditions**
- explicit conditions under which guarded downstream execution is still acceptable

**Fail criteria**
- explicit conditions that prevent readiness for the named downstream use

**Remediation actions**
- concrete next actions to improve readiness

**Recording expectations**
- what minimum result data must be stored so later steps can trace the decision

Authors should keep gate language specific to the downstream boundary being protected. Do not write generic criteria that sound rigorous but do not change the decision.

## Non-Negotiable Rules

- Every gate must name its gate subject explicitly.
- Every gate must define explicit meaning for `pass`, `conditional pass`, and `fail`.
- Every gate result must be recorded and remain traceable to the evaluated artifact state.
- No gate may grant a clean pass to a stale artifact for the target downstream use.
- No gate may grant a clean pass to an incompatible artifact for the target downstream use.
- No downstream skill may silently continue as though readiness were established after a failed gate.
- Conditional passes must record inherited uncertainty and why downstream execution is still acceptable.
- Gates evaluate readiness for a named next step, not perfection in general.

## Quick Compliance Checklist

- Is the gate name explicit and stable?
- Is the gate subject explicit?
- Was the latest compatible artifact selected before evaluation?
- Were lifecycle, compatibility, assumptions, and open questions considered?
- Are pass, conditional pass, and fail defined operationally?
- Are pass criteria visible and specific?
- Are fail criteria visible and specific?
- Are conditional-pass conditions explicit and bounded?
- Are remediation actions concrete?
- Is the recorded result traceable to a specific artifact version or update state?
- Does the gate avoid a clean pass for stale or incompatible artifacts?
- Will downstream skills know whether they may proceed normally, proceed with caveats, or stop?
