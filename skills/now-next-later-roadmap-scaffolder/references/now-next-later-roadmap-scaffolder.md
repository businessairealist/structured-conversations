# Now Next Later Roadmap Scaffolder

## Purpose
Create a goal-oriented roadmap board with Now, Next, Later, and product outcome areas rather than a date-driven feature list.

## Use This When
- You need a poster-style roadmap artifact.
- The team wants to communicate sequencing by confidence and outcome linkage.
- Customer needs and product outcomes should stay visible beside initiatives.

## Required Inputs
- Title.
- Goal.

## Optional Inputs
- `now`, `next`, and `later` initiative lists.
- Product outcomes.
- Customer-needs outcomes.

## Script

## Artifact Shape
- Collection: `strategy-experimentation`
- Artifact type: `now_next_later_roadmap_artifact`
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
  --title "Restaurant Menu Expansion" `
  --goal "Increase weeknight order frequency for families by 40% in 6 months" `
  --now-json "[\"Simplify weeknight ordering\",\"Weeknight family meal deals\"]"
```
