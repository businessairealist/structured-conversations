# User Intent Routing

## Purpose

This file maps common user intents to the kinds of skills the workspace should suggest first.

## Intents

- Clarify an idea:
  Use foundation routing skills such as `verb-noun-rewriter`, `syntax-pattern-selector`, or `structured-conversation-facilitator`.
- Map a workflow:
  Use discovery skills such as `user-story-map-builder`, `customer-journey-map-builder`, `impact-map-builder`, or `value-stream-map-builder`.
- Shape a concept:
  Use vision skills such as `future-press-release-writer`, `product-elevator-pitch-writer`, or `persona-pitch-adapter`.
- Define requirements:
  Use specification skills such as `feature-map-builder`, `example-map-builder`, `acceptance-criteria-scaffolder`, or `gherkin-scenario-writer`.
- Plan delivery work:
  Use delivery skills such as `user-story-drafter`, `story-splitting-method-selector`, `user-story-splitter`, or `story-subtask-planner`.
- Capture a defect:
  Use quality skills such as `defect-report-writer`, `defect-reproduction-scaffolder`, or `severity-priority-classifier`.
- Build strategy plans:
  Use strategy skills such as `goal-oriented-roadmap-builder`, `okri-builder`, or `hypothesis-experiment-designer`.

## User-Facing Framing

When routing the user, prefer the language of the job to be done over the language of the skill catalog.

- Say "map the workflow" instead of "run a mapping skill".
- Say "turn this into testable behavior" instead of "generate a downstream artifact".
- Say "choose the next planning step" instead of "select the next compatible artifact" unless technical precision is required.
