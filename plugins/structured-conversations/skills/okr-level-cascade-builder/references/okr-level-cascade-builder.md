# OKR Level Cascade Builder

## Purpose
Create a multi-level OKR cascade that shows how company, regional, team, or store-level objectives align through key results and initiatives.

## Use This When
- You need a board showing OKR alignment across organizational levels.
- Teams need to see how lower-level work supports higher-level outcomes.
- A poster-style cascade is more useful than isolated OKRs.

## Required Inputs
- Title.
- `levels_json` list of objects with `level`, `objective`, and optional `key_results` and `initiatives`.

## Script

## Artifact Shape
- Collection: `strategy-experimentation`
- Artifact type: `okr_level_cascade_artifact`
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
  --title "Objectives and Key Results" `
  --levels-json "[{\"level\":\"Company\",\"objective\":\"Grow fastest in market\"},{\"level\":\"Regional\",\"objective\":\"Achieve profitability\"}]"
```
