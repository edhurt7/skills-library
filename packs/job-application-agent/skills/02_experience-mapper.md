---
name: experience-mapper
description: Maps candidate experience to role requirements and identifies gaps.
inputs:
  - name: role_spec
    type: object
  - name: candidate_profile
    type: object
outputs:
  - name: mapping
    type: object
  - name: gaps
    type: list
  - name: do_not_claim
    type: list
version: 0.1.0
tags:
  - job-application-agent
  - mapping
  - gap-analysis
---

# Experience Mapper

## Goal

Align candidate experience to the role specification, identify gaps, and explicitly mark unsupported claims.

## Steps

1. Read `role_spec` and list required and preferred qualifications as checkpoints.
2. Match candidate evidence to each checkpoint with citations to resume sections or notes.
3. Produce `mapping` with: requirement, evidence, strength, and assumption flag.
4. List missing items as `gaps` with a neutral description.
5. Populate `do_not_claim` with tools, metrics, credentials, or employers not supported by evidence.

## Rules

- Never fabricate tools, credentials, metrics, or employers.
- When info is missing, label assumptions.
- Outputs must be structured and easy to paste into the next step.

## Failure Modes

- Overstating experience strength or failing to mark assumptions.
- Mixing preferred items into required items without labels.
- Leaving `do_not_claim` empty when evidence is thin.
