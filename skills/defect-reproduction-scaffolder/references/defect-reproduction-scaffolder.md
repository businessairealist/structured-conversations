# Defect Reproduction Scaffolder

## Purpose
Turn a failure observation into a reproducible path with setup, ordered steps, expected result, actual result, and reproducibility status.

## Use This When
- The team needs clearer reproduction steps before triage or debugging.
- A defect report exists but the path to recreate the failure is weak.
- You want a reusable canonical reproduction artifact.

## Required Inputs
- A failure observation.

## Optional Inputs
- Environment details.
- Setup or prerequisite data.
- Ordered steps.
- Expected and actual result.
- Reproducibility rating.

## Script

## Artifact Shape
- Collection: `quality-diagnostics`
- Artifact type: `defect_reproduction_artifact`
- Canonical root: the working directory<slug>/`
- Required files:
  - the structured markdown output
  - the human-readable summary
  - execution notes
  - source traceability notes
  - open questions

## Content Expectations
The canonical payload should include:
- observation
- environment
- setup
- steps to reproduce
- expected result
- actual result
- reproducibility

## Minimal CLI Example
```powershell
  --project-root D:\work\project `
  --observation "Saved payment details fail to load" `
  --setup "Log in as a returning customer with a saved card" `
  --expected "Saved payment details prefill the form" `
  --actual "Form remains blank"
```
