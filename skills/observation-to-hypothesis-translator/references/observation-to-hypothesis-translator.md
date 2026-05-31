# Observation To Hypothesis Translator

## Purpose
Translate an observation into competing hypotheses with downstream experiments, measurable signals, pass/fail logic, and data-driven decisions.

## Use This When
- The team has an observation but not yet a testable set of explanations.
- You want a hypothesis tree artifact rather than loose notes.
- Experiments and decisions should be visible under each branch.

## Required Inputs
- Observation.
- Desired outcome.

## Optional Inputs
- A prebuilt hypotheses JSON structure.

## Script

## Artifact Shape
- Collection: `strategy-experimentation`
- Artifact type: `hypothesis_tree_artifact`
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
  --observation "Our weeknight business is 50% slower than weekends" `
  --desired-outcome "Increase weeknight orders"
```
