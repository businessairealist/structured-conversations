---
name: shared-contracts
render_family: form
description: "Explain the shared conventions that govern how structured conversation artifacts are organized, versioned, and chained together. Use when you need guidance on artifact naming, quality gates, evidence normalization, dependency recipes, or update integrity."
---

# Shared Contracts and Conventions

Provide guidance on the architectural contracts that govern how structured conversation
artifacts are created, named, versioned, updated, and chained together.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

## Core Contracts Available

Read the relevant reference file from `references/` when the user asks about:

- **Artifact schema** - structured output package structure (`artifact-schema.md`)
- **output lifecycle** - versioning, supersession, compatibility (`artifact-lifecycle.md`)
- **Artifact naming** - kebab-case slugs, deterministic naming (`artifact-naming-conventions.md`)
- **Artifact locations** - where artifacts live and how to find them (`artifact-location-rules.md`)
- **Project layout** - standard folder scaffold (`project-layout.md`)
- **workspace conventions** - runtime expectations (`workspace-contract.md`)
- **Dependency recipes** - how skills chain together (`dependency-recipes.md`)
- **Evidence normalization** - normalizing raw inputs (`evidence-normalization.md`)
- **Quality gates** - readiness checks for handoffs (`quality-gates.md`)
- **Update integrity** - safe change semantics (`update-integrity-rules.md`)
- **Render contract** - rendering behavior families (`render-contract.md`)
- **User intent routing** - mapping intents to skill families (`user-intent-routing.md`)
- **User interaction contract** - user-facing language rules (`user-interaction-contract.md`)

When answering, cite the specific contract and explain it in practical terms.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

- Output is complete and self-contained — a reader can act on it without additional context
- Evidence and sources are cited, not invented
- Open questions and assumptions are called out explicitly
- Structure follows the conventions for this artifact type

