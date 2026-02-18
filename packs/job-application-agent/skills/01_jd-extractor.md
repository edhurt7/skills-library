---
name: jd-extractor
description: Extracts a structured role specification from a job description.
inputs:
  - name: job_description
    type: text
outputs:
  - name: role_spec
    type: object
version: 0.1.0
tags:
  - job-application-agent
  - extraction
  - role-spec
---

# JD Extractor

## Goal

Transform an unstructured job description into a normalized, machine-readable role specification for downstream steps.

## Steps

1. Parse the job description and identify: role title, seniority, domain, location/remote, employment type, and company context.
2. Extract responsibilities, required qualifications, preferred qualifications, and explicit keywords.
3. Derive implicit requirements (e.g., collaboration, ownership) and label them as inferred.
4. Produce `role_spec` with stable keys and short, reusable phrases.

## Rules

- Never fabricate tools, credentials, metrics, or employers.
- When info is missing, label assumptions.
- Outputs must be structured and easy to paste into the next step.

## Failure Modes

- Missing responsibilities or qualifications due to overly aggressive summarization.
- Inferred requirements presented as explicit.
- Non-standard or inconsistent key names that break downstream parsing.
