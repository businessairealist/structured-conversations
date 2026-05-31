# Objective Key Result Initiative Scaffolder

## Purpose
Create a single-level OKR board that connects one objective to measurable key results and the initiatives expected to move them.

## Use This When
- You want an OKR map rather than a prose-only OKRI record.
- The team needs a board that links work to outcomes at one level.
- An objective exists but its key results or initiatives need structure.

## Required Inputs
- Objective.

## Optional Inputs
- Key results list.
- Initiatives list.

## Script

## Artifact Shape
- Collection: `strategy-experimentation`
- Artifact type: `objective_keyresult_initiative_artifact`
- Canonical root: the working directory<slug>/`
- Required files:
  - the structured markdown output
  - the human-readable summary
  - execution notes
  - source traceability notes
  - open questions

## Minimal CLI Example
```powershell
  --project-root D:\work\project `
  --objective "Increase weeknight business" `
  --key-results-json "[\"Increase repeat orders by 25%\",\"Increase weeknight revenue by 50%\"]"
```
