---
name: structured-conversation-facilitator
render_family: form
description: Turn a vague cross-functional topic into a structured conversation plan that uses precise language, the right mapping technique, and clear facilitation moves to reach shared outcomes. Use when you need to plan or run alignment conversations, discovery workshops, backlog clarification, framing sessions, or stakeholder discussions that start fuzzy and need a guided path to a concrete artifact.
---

# Structured Conversation Facilitator

Use this skill to turn ambiguity into a conversation plan that can be executed independently inside a workspace.


Keep the skill focused on facilitation and routing. Use sibling skills when the conversation needs a deeper artifact:

- Use `verb-noun-rewriter` to tighten vague nouns or overloaded statements.
- Use `syntax-pattern-selector` to choose the best requirement or hypothesis syntax.
- Use `mapping-technique-selector` to choose the most useful map or workshop format.

Read [structured-conversation-facilitator.md](././references/foundation/structured-conversation-facilitator.md) for the facilitation blueprint, question bank, and output template.

Read these shared references when project-runtime details matter:

- [workspace-contract.md](././references/shared/workspace-contract.md)
- [artifact-location-rules.md](././references/shared/artifact-location-rules.md)
- [artifact-schema.md](././references/shared/artifact-schema.md)
- [render-contract.md](././references/shared/render-contract.md)

## Find Inputs

Treat these as required inputs:

- A vague topic, problem, requirement, initiative, or conversation prompt.
- Enough context to understand who needs alignment and what decision or output is needed.

Treat these as optional inputs:

- Audience, facilitator stance, meeting duration, or workshop format.
- Existing notes, prior artifacts, constraints, or preferred downstream artifact type.

Resolve inputs in this order:

1. Explicit artifact or path arguments from the user request.
3. `intake/`
4. `inputs/notes/`
5. `artifacts/shared/`
6. `artifacts/foundation/`

If the topic is still under-specified after the search, ask only for the smallest missing piece: the topic, audience, or intended outcome.

## Run the Facilitation Workflow

Use this sequence:

1. Frame the topic in plain language.
2. Identify the conversation goal, target artifact, participants, and decision horizon.
3. Rewrite fuzzy language into precise verb-plus-object statements when needed.
4. Choose the best conversation structure:
   - framing and language alignment
   - requirement syntax selection
   - mapping workshop selection
   - escalation to a downstream artifact-building skill
5. Draft a facilitation plan with opening prompt, question sequence, synthesis checkpoints, and closing output.
6. Record assumptions, unresolved questions, and recommended next skills.

Prefer short, high-signal dialogue prompts over generic brainstorming questions.

Stop and ask for clarification instead of guessing when:

- the request mixes multiple unrelated problems,
- the desired output is ambiguous,
- the conversation would require choosing between incompatible artifact families,
- or a structural change would break compatibility with an upstream artifact.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the plan:

- narrows ambiguity instead of restating it,
- produces a visible next artifact or decision,
- uses the smallest adequate workshop structure,
- preserves traceability to source inputs and upstream artifacts,
- and stays reusable by downstream foundation, mapping, or specification skills.

If the best answer is that the user should skip facilitation and go straight to a specific downstream skill, say so clearly and make that recommendation part of the artifact.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- This skill is an explicit opt-in path. Do not use it as a silent fallback when a real artifact request is missing prerequisites.
- Treat this skill as a natural-language starting point for users who do not know which artifact comes first.
- Keep the user on readable facilitation outputs rather than backend package files.
- After generation, explain what to review and recommend the most likely downstream artifact or decision.
