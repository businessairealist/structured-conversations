# Syntax Pattern Selector Reference

## Purpose

Use this reference to choose the best framing pattern for a requirement, hypothesis, rule, or delivery conversation and to draft the statement in that format.

This reference focuses on how to choose among patterns, not project-runtime mechanics.

## Core Outcome

A good selection does all of the following:

- matches the syntax to the real decision or conversation need
- explains why the selected pattern fits
- produces a usable draft in that pattern
- records rejected alternatives only when they help
- leaves downstream work with clearer framing

## Default Selection Flow

Use this sequence unless the request is already tightly constrained:

1. Capture the source context.
2. Identify audience and delivery need.
3. Determine whether the need is requirement, hypothesis, job-to-be-done, feature clarification, rule definition, or constraint framing.
4. Compare the relevant syntax patterns.
5. Select the best-fit pattern.
6. Draft the statement.
7. Record tradeoffs, assumptions, and open questions.

## Selection Heuristics

- Choose the smallest pattern that makes the decision clearer.
- Prefer problem-focused patterns for discovery.
- Prefer behavior- or rule-focused patterns for specification.
- Prefer audience-sensitive patterns when stakeholder interpretation matters.
- Route to `verb-noun-rewriter` first when the source wording is still too fuzzy.

## Output Template

Use this shape in the structured markdown output.content` and mirror it in the human-readable summary:

- `source_context`
- `audience`
- `delivery_context`
- `candidate_patterns`
- `selected_pattern`
- `selection_rationale`
- `draft_statement`
- `rejected_alternatives`
- `assumptions`
- `open_questions`

## Failure Modes

Avoid these patterns:

- picking a format because it is familiar rather than useful
- drafting multiple patterns when one clear recommendation is enough
- treating syntax as cosmetic when it changes what teams optimize for
- leaving the draft so abstract that a downstream skill still has to reinterpret it
