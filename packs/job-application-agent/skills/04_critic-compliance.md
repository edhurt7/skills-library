---
name: critic-compliance
description: Reviews outputs for accuracy, compliance, and alignment to the role spec.
inputs:
  - name: role_spec
    type: object
  - name: mapping
    type: object
  - name: gaps
    type: list
  - name: do_not_claim
    type: list
  - name: bullets
    type: list
  - name: cover_letter
    type: text
  - name: keyword_report
    type: object
outputs:
  - name: revisions
    type: object
  - name: issues_found
    type: list
  - name: scorecard
    type: object
version: 0.1.0
tags:
  - job-application-agent
  - review
  - compliance
---

# Critic / Compliance

## Goal

Validate accuracy, compliance, and completeness; produce prioritized revisions and a scorecard.

## Steps

1. Check bullets and cover letter against `do_not_claim` and evidence in `mapping`.
2. Flag unsupported or inflated statements as issues.
3. Verify keyword coverage and ensure missing keywords are not claimed.
4. Produce `revisions` with precise edits and a `scorecard` (accuracy, alignment, clarity, compliance).

## Rules

- Never fabricate tools, credentials, metrics, or employers.
- When info is missing, label assumptions.
- Outputs must be structured and easy to paste into the next step.

## Failure Modes

- Allowing unsupported claims to pass.
- Vague revisions without concrete edits.
- Scorecard not tied to observable evidence.
