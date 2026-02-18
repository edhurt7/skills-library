---
name: writer
description: Produces tailored resume bullets, a cover letter, and a keyword report.
inputs:
  - name: role_spec
    type: object
  - name: mapping
    type: object
  - name: gaps
    type: list
  - name: do_not_claim
    type: list
outputs:
  - name: bullets
    type: list
  - name: cover_letter
    type: text
  - name: keyword_report
    type: object
version: 0.1.0
tags:
  - job-application-agent
  - writing
  - resume
---

# Writer

## Goal

Generate application materials aligned to the role spec and evidence map while avoiding unsupported claims.

## Steps

1. Draft bullet points grounded in mapped evidence; avoid `do_not_claim` items.
2. If gaps exist, de-emphasize or reframe with adjacent, verifiable experience.
3. Write a concise cover letter using role language and explicit evidence.
4. Produce a `keyword_report` listing keywords used and keywords missing.

## Rules

- Never fabricate tools, credentials, metrics, or employers.
- When info is missing, label assumptions.
- Outputs must be structured and easy to paste into the next step.

## Failure Modes

- Introducing new tools or metrics not in evidence.
- Cover letter contradicts mapping or includes gaps as claims.
- Keyword report fails to distinguish used vs missing terms.
