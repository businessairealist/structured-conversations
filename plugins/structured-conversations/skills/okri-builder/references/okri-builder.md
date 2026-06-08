# OKRI Builder

## Purpose
Create a structured OKRI record that connects one objective to measurable key results and the initiatives intended to move them.

## Use This When
- You need a form-style OKRI record.
- An OKR exists but the initiative layer is missing.
- You want a canonical strategy artifact for later review or conversion into a board.

## Required Inputs
- Objective.

## Optional Inputs
- Key results list.
- Initiatives list.
- Review cadence.

## Script

## Artifact Shape
- Collection: `strategy-experimentation`
- Artifact type: `okri_record_artifact`
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
  --key-results-json "[\"Increase repeat orders by 25%\"]" `
  --initiatives-json "[\"Launch a weeknight meal bundle\"]"
```
