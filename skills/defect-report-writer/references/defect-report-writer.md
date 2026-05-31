# Defect Report Writer

## Purpose
Turn an observed failure into a triage-ready defect report with impact, environment, steps to reproduce, expected behavior, and actual behavior.

## Use This When
- A failure has been observed but the report is incomplete or inconsistent.
- QA, engineering, or product needs a reusable canonical defect artifact.
- You want a form-style artifact instead of scattered notes.

## Required Inputs
- A defect observation or raw failure summary.

## Optional Inputs
- Environment details.
- Reproduction steps.
- Expected and actual behavior.
- Severity or priority hints.
- Supporting notes, screenshots, or logs discovered through project search.

## Script

## Artifact Shape
- Collection: `quality-diagnostics`
- Artifact type: `defect_report_artifact`
- Canonical root: the working directory<slug>/`
- Required files:
  - the structured markdown output
  - the human-readable summary
  - execution notes
  - source traceability notes
  - open questions

## Content Expectations
The canonical payload should include:
- defect title
- observation
- impact
- environment
- ordered reproduction steps
- expected behavior
- actual behavior
- optional severity and priority

## Minimal CLI Example
```powershell
  --project-root D:\work\project `
  --observation "Checkout freezes after clicking Pay Now" `
  --impact "Customers cannot complete checkout" `
  --environment "Production, Chrome 123, desktop" `
  --expected "Order submits successfully" `
  --actual "Spinner never resolves"
```
