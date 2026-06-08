# Hypothesis Experiment Designer

## Purpose
Turn a hypothesis into a decision-ready experiment with signals, pass criteria, fail criteria, and next-step decisions.

## Use This When
- A hypothesis exists and needs an experiment plan.
- The team needs success and failure logic before investing further.
- You want a canonical experiment artifact instead of ad hoc notes.

## Required Inputs
- Hypothesis.
- Experiment.
- Desired outcome.

## Optional Inputs
- Signals list.
- Pass criteria.
- Fail criteria.
- Decision if pass.
- Decision if fail.

## Script

## Artifact Shape
- Collection: `strategy-experimentation`
- Artifact type: `hypothesis_experiment_artifact`
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
  --hypothesis "Prepared family meals make weeknights easier for families" `
  --experiment "Offer a limited prepared family meal bundle" `
  --desired-outcome "Increase repeat weeknight orders"
```
