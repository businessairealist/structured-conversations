# Code Review To Subtask Translator

Convert review findings or change-plan notes into actionable subtasks with clear traceability.

## Use When

- a code review already identified defects, risks, or change requests
- a team needs to turn review feedback into implementation work
- `story-subtask-planner` would be too broad because the source is review-oriented rather than story-oriented

## Input Expectations

Preferred inputs:

- review comments
- inline review findings copied into notes
- change-plan bullets
- supporting story or acceptance artifacts when available

Useful signals to preserve:

- file or component references
- severity or risk language
- explicit validation or regression concerns
- recommended fix direction

## Translation Workflow

1. Normalize the findings into distinct issues.
2. Preserve any file, component, or risk context that affects implementation.
3. Group findings only when the implementation work is truly shared.
4. Produce concrete subtasks plus testing or validation follow-up.
5. Record open questions when the review note is not specific enough to implement safely.

## Expected Output Shape

Create a delivery artifact that includes:

- findings board or grouped review issues
- implementation ideas or change clusters
- delivery-ready subtasks
- dependency hints
- validation follow-up
- open questions

## Good Output Characteristics

- each subtask maps back to one or more findings
- the work is implementation-ready, not just a copy of review comments
- risky findings remain visible
- testing and regression coverage are explicit
