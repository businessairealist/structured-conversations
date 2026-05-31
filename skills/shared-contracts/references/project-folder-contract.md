# Workspace Conventions

## Purpose

This file defines how skills operate within a user's workspace in Claude/Cowork. It ensures consistency, discoverability, and safe output handling across all skills.

## Scope

This file governs: how a skill discovers inputs, where it writes outputs, and how it interacts with existing workspace content. It does not define visual rendering, artifact schemas, or naming — those belong in sibling references.

## Workspace Model

In the Claude/Cowork environment, a workspace is the user's selected folder (or the conversation's working directory). Skills operate within this space to read inputs and write outputs.

There is no artifact registry, no run manifest system, no index.json files, and no bootstrap scaffold. Skills should work with whatever folder structure the user has.

## Input Discovery

Before asking the user for inputs, a skill should:

1. Check if the user provided files, notes, or prior artifacts in the current conversation
2. Look for related outputs from earlier skills in the workspace
3. Search the workspace for files matching expected naming patterns
4. Only ask for missing information that cannot be reasonably inferred

When multiple plausible inputs exist, present a short human-friendly choice based on title, topic, and recency.

## Output Placement

Save outputs to the user's workspace or selected folder. Standard output expectations:

- A structured markdown document with the primary content
- Any supporting artifacts (diagrams, tables, summaries) as separate files if needed
- An HTML rendering when visual layout adds significant value

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Traceability

When a skill builds on a prior artifact:

- Note which source materials or prior outputs were used
- Preserve the connection between input evidence and output claims
- Call out assumptions and open questions explicitly

## Update Safety

When updating an existing artifact:

- Change only the requested sections
- Preserve unchanged content
- If the requested change would require restructuring the whole artifact, ask for clarification

## Independent Invocation

Every skill must work correctly when called on its own. Do not assume a previous skill prepared the workspace. Verify that needed inputs exist before proceeding.

## Relationship to Other References

- `artifact-schema.md` — field expectations for structured outputs
- `artifact-naming-conventions.md` — naming rules for files and slugs
- `evidence-normalization.md` — how source evidence should be represented
- `quality-gates.md` — quality standards for outputs
