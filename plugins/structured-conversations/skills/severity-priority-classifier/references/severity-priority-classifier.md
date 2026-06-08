# Severity Priority Classifier

## Purpose
Recommend severity and priority values for a defect while preserving the rationale and uncertainty behind the classification.

## Use This When
- A defect needs a consistent severity and priority recommendation.
- You want to capture triage reasoning in a structured output.
- Scope, urgency, and workaround availability matter to the decision.

## Required Inputs
- A defect summary or report.

## Optional Inputs
- Scope of impact.
- Workaround availability.
- Release or operational urgency.
- Team-specific rubric overrides.

## Script

## Artifact Shape
- Collection: `quality-diagnostics`
- Artifact type: `severity_priority_classification_artifact`
- Canonical root: the working directory<slug>/`
- Required files:
  - the structured markdown output
  - the human-readable summary
  - execution notes
  - source traceability notes
  - open questions

## Content Expectations
The canonical payload should include:
- summary
- scope
- workaround
- urgency
- recommended severity
- recommended priority
- rationale

## Minimal CLI Example
```powershell
  --project-root D:\work\project `
  --summary "Checkout freezes during payment submission" `
  --scope "Multiple customers in production" `
  --workaround "none" `
  --urgency "high"
```
