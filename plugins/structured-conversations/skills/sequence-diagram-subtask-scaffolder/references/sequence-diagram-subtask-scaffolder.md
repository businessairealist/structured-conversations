# Sequence Diagram Subtask Scaffolder

Use an interaction flow or sequence diagram to derive technical implementation subtasks.

## Use When

- a team already understands the main request and response flow
- the next step is technical decomposition across layers
- sequence order matters for implementation, retries, side effects, or validation

## Good Inputs

- participant-to-participant interaction notes
- Mermaid or text sequence steps
- request/validation/persistence/response bullets
- supporting story or acceptance artifacts

## Scaffolding Workflow

1. Identify participants and ordered interactions.
2. Preserve the main decision, validation, and side-effect points.
3. Turn interaction clusters into implementation subtasks.
4. Add validation or regression follow-up.
5. Record open questions where the sequence is incomplete.

## Expected Output Shape

Create a delivery artifact with:

- participants
- ordered sequence steps
- technical subtasks grouped from the flow
- dependency or ordering hints
- testing follow-up
- open questions

## Good Output Characteristics

- the flow remains traceable after decomposition
- subtasks map to real interaction boundaries
- validation, persistence, and external effects are explicit
- missing sequence detail becomes an open question instead of a guess
