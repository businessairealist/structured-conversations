# Structured Conversation Facilitator Reference

## Purpose

Use this reference to convert a fuzzy topic into a conversation plan that creates alignment and routes the team toward the right next artifact.

This reference is for facilitation structure, not project-runtime mechanics. Read the shared references when you need path, schema, rendering, or lifecycle details.

## Core Outcome

A good structured conversation produces all of the following:

- a tighter statement of the problem or opportunity
- a clear target outcome or decision
- a recommended conversation structure
- a concrete next artifact, next skill, or next action
- explicit assumptions and open questions

If the conversation does not make the next step clearer, it is not structured enough yet.

## Default Conversation Arc

Use this arc unless the request strongly suggests a different order:

1. Name the topic.
2. Identify who needs alignment.
3. Define the desired outcome or decision.
4. Tighten vague language.
5. Choose the best structure for the conversation.
6. Ask the minimum questions needed to unlock progress.
7. Synthesize the output into a reusable artifact.

## Structure Selection Guide

Choose the lightest structure that will still move the work forward.

### Use language alignment first

Use this when the request contains vague nouns, broad initiatives, or overloaded backlog items.

Signs:

- people are talking past each other
- the topic is a pile of nouns rather than an action
- the team cannot tell whether the request is a feature, problem, outcome, or deliverable

Typical next move:

- rewrite into one or more precise verb-plus-object statements
- separate mixed concerns before choosing a downstream artifact

### Use syntax selection next

Use this when the team knows the topic but not the right framing pattern.

Signs:

- the group is debating story versus hypothesis versus requirement language
- stakeholders need the same idea expressed differently for different decisions
- the main blocker is format, precision, or audience fit

Typical next move:

- choose a syntax pattern
- draft the statement in that syntax
- capture rejected alternatives only when they clarify tradeoffs

### Use mapping technique selection next

Use this when the issue needs structure across actors, flow, rules, opportunities, or delivery slices.

Signs:

- the discussion spans multiple people, steps, or dependencies
- the team needs a visual artifact to align
- sequencing, scope, or cause-and-effect matters more than sentence polish

Typical next move:

- select a map family
- explain why it fits the problem
- route to the right mapping or facilitation skill

## Question Bank

Ask only the questions needed to remove the main ambiguity.

### Framing questions

- What is the topic in one sentence?
- What feels unclear or contested right now?
- Who needs to agree before work can move?
- What must be true when this conversation is done?

### Outcome questions

- Are we trying to make a decision, create an artifact, or expose open questions?
- What will this conversation unlock next?
- What would count as a useful output by the end?

### Precision questions

- Which words in the request are doing too much work?
- What action should someone be able to take after this is clarified?
- Is the request really one thing, or several bundled together?

### Routing questions

- Do we need a better sentence, a better map, or a better workshop?
- Is the blocker language, structure, evidence, or scope?
- Which downstream artifact would create the most leverage next?

## Output Template

Use this shape in the structured markdown output.content` and mirror it in the human-readable summary:

- `topic`
- `current_problem`
- `target_outcome`
- `participants`
- `recommended_structure`
- `facilitation_steps`
- `question_sequence`
- `decision_points`
- `next_artifact_or_skill`
- `assumptions`
- `open_questions`

## Facilitation Heuristics

- Prefer one strong next artifact over a long list of options.
- Prefer a small number of exact prompts over broad brainstorming.
- Split mixed requests before selecting a structure.
- Route quickly when a sibling skill can do the heavy lifting better.
- Preserve source traceability so downstream skills can reuse the result safely.

## Failure Modes

Avoid these patterns:

- repeating the user request without reducing ambiguity
- jumping into a large workshop format too early
- inventing missing context instead of surfacing it as an open question
- producing a facilitation plan with no concrete output
- choosing a visual render that adds style but not clarity
