---
name: user-story-drafter
render_family: form
description: Draft and strengthen user stories in the right syntax. Use when you need to turn a requirement, epic slice, mapped insight, or rough backlog note into a clearer user story with actor, behavior, value, assumptions, and readiness notes that downstream INVEST, example-mapping, and subtasking work can use.
---

# User Story Drafter

Draft a user story in the best-fit syntax, then strengthen it until it is specific enough for downstream work.


Use this skill after story maps, release slices, impact outputs, feature maps, or pitch-to-epic flows. Use `invest-readiness-checker` after drafting when the story needs a formal readiness assessment.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a work item, mapped opportunity, epic slice, or rough story seed
- enough context to identify actor, behavior, and intended outcome

Optional inputs:

- preferred story format
- constraints, acceptance hints, or example-map context
- release slice, hypothesis signal, or business rule emphasis
## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Try to locate the strongest existing story seed, release slice, or mapped artifact before asking the user for new wording.
- If multiple plausible sources exist, present a short choice list with topic and recency.
- Show the draft through its readable artifact surface and keep registry or manifest files out of the normal user flow.
- After generation, recommend acceptance criteria, example mapping, or story splitting based on the draft quality.

## Draft The Story

Use this sequence:

1. Normalize the request into a clear work item.
2. Select or confirm the story format.
3. Draft the story with actor, behavior, and value or equivalent fields for the chosen syntax.
4. Add the minimum useful context needed for estimation, testing, and example mapping.
5. Record assumptions and unresolved questions instead of hiding them inside vague prose.
6. Call out whether the story appears ready for `story_ready_for_example_mapping`.

Prefer concise stories with explicit downstream notes over bloated pseudo-specs.

Strengthen weak drafts by:

- replacing vague verbs with observable behavior,
- making the benefit or measurable signal explicit,
- separating true unknowns into `open_questions`,
- and surfacing likely split points instead of stuffing too much scope into one story.

Stop and ask for clarification when the story would otherwise invent the actor, primary outcome, or key domain rule.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

Capture at least:

- source context and upstream artifacts
- chosen syntax
- drafted story
- supporting detail or readiness notes
- assumptions
- open questions
- possible next skills

Render HTML only when the user wants a review-friendly draft card or comparison sheet.

## Handoff Rules

When the story is solid enough for clarification work, route toward `example-map-builder` and record whether `story_ready_for_example_mapping` appears to pass.

When the story is solid enough for implementation planning, record whether `story_ready_for_subtasking` appears to pass and route toward `story-subtask-planner`.

When the draft is still too broad, route toward `story-splitting-method-selector` or `user-story-splitter`.

## Quality Bar

Ensure the draft:

- is concrete enough to discuss with a team,
- stays small enough that splitting decisions remain visible,
- carries forward uncertainty honestly,
- and improves the starting material instead of merely reformatting it.

Tell the user to review:

- whether the actor and goal are right,
- whether the value statement is concrete enough,
- and whether the draft should be clarified, split, or taken forward.
