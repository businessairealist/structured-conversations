# Verb-Noun Rewriter Reference

## Purpose

Use this reference to convert vague statements into precise action-plus-object language and to split overloaded requests into smaller units that downstream skills can consume.

This reference focuses on rewrite behavior, not project-runtime mechanics.

## Core Outcome

A good rewrite does all of the following:

- states an observable action
- names the object of that action
- removes bundled or fuzzy scope
- keeps traceability to the source wording
- leaves a cleaner next step for a downstream artifact

## Default Rewrite Flow

Use this sequence unless the request clearly needs a lighter pass:

1. Capture the original wording.
2. Identify vague nouns, weak verbs, and bundled intents.
3. Infer the likely action without adding hidden requirements.
4. Rewrite into one or more verb-plus-noun statements.
5. Split the item if it contains multiple actions or deliverables.
6. Record assumptions and open questions.

## Output Template

Use this shape in the structured markdown output.content` and mirror it in the human-readable summary:

- `original_statement`
- `source_context`
- `rewrite_candidates`
- `recommended_rewrites`
- `decomposition`
- `assumptions`
- `open_questions`

## Decomposition Rules

Split the source into multiple items when any of these are true:

- one statement hides multiple user or system actions
- one statement mixes outcome, implementation, and reporting
- one statement combines more than one deliverable
- one statement contains conjunctions that change the action surface

Keep decomposed items parallel in style and scope.

## Decision Heuristics

- Prefer strong verbs that imply observable completion.
- Prefer concrete objects over category words such as `stuff`, `management`, or `support`.
- Prefer several small rewrites over one overloaded rewrite.
- Preserve the original meaning even when the original phrasing is poor.
- Surface uncertainty as an open question instead of pretending precision.

## Failure Modes

Avoid these patterns:

- replacing one vague noun with another vague noun
- adding scope that was never implied by the source
- keeping a single rewrite when the source clearly needs splitting
- choosing elegant wording over operational clarity
