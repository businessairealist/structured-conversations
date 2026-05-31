---
name: empathy-insight-extractor
render_family: form
description: Distill a completed empathy map into pains, gains, tensions, opportunities, and implications. Use when you need to summarize a rich empathy map into the strongest downstream planning signals.
---

# Empathy Insight Extractor

Extract the most useful pains, gains, tensions, opportunities, and implications from a completed empathy map.


Use this skill after `empathy-map-builder` or `empathy-map-facilitator` when the team needs a tighter summary that can feed downstream planning or prioritization work.

## Find Inputs Before Asking

Before asking the user for inputs, check whether relevant material already exists:

1. Check if the user provided files, notes, or prior artifacts in this conversation
2. Look for related outputs from earlier skills in the workspace
3. Only ask for missing information that cannot be reasonably inferred

Required inputs:

- a completed empathy-map artifact

Optional inputs:

- a specific empathy-map artifact id or slug
- context about which downstream planning decision matters most
## Extract The Insights

Use this sequence:

1. Load the empathy-map cards and preserve their section origin.
2. Distill the strongest pain, gain, tension, opportunity, and implication signals.
3. Keep clear traceability from each insight back to the source section.
4. Mark questions or inferred content explicitly when the evidence is weak.

Use the output to sharpen downstream prioritization, mapping, or experimentation work rather than replacing the original empathy map.

## Write Outputs

Save the result to the user's workspace or selected folder. Produce:

1. A structured markdown document with the primary content
2. Any supporting artifacts (diagrams, tables, summaries) as separate files if needed

Name files using kebab-case descriptive slugs (e.g., `checkout-flow-empathy-map.md`).

## Quality Bar

Ensure the output:

- preserves traceability to the empathy map,
- separates evidence-backed insights from inference,
- surfaces the strongest downstream opportunities,
- and stays concise enough to guide action.

## User Experience Contract

- Speak to the user in plain language centered on their goal, the concrete map, draft, plan, report, or scenario set being created, and the next useful step.
- Prefer the concrete deliverable name over generic system terms like artifact, canonical package, compatible output, or generator unless technical detail is necessary.
- When prerequisites are missing, frame the gap as "what I need from you" and explain the smallest useful next action.
- Locate the best existing project content for this skill before asking the user to paste, restate, or re-upload it.
- If more than one plausible draft, map, note set, or saved plan matches, present a short human-friendly choice based on title, topic, and recency.
- Keep the user on readable maps, drafts, plans, reports, and previews rather than backend manifests, indexes, or internal runtime files.
- After generation, explain what the user should review and suggest the most likely next step for the artifact.
