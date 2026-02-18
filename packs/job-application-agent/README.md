# Job Application Agent

## What It Does

A structured, multi-step workflow that converts a job description and candidate profile into tailored application materials with compliance checks.

## Components

- `01_jd-extractor.md`: produces `role_spec`.
- `02_experience-mapper.md`: produces `mapping`, `gaps`, `do_not_claim`.
- `03_writer.md`: produces `bullets`, `cover_letter`, `keyword_report`.
- `04_critic-compliance.md`: produces `revisions`, `issues_found`, `scorecard`.

## Orchestration

1. Run JD Extractor on the job description to obtain `role_spec`.
2. Run Experience Mapper with `role_spec` and `candidate_profile`.
3. Run Writer with `role_spec`, `mapping`, `gaps`, and `do_not_claim`.
4. Run Critic/Compliance with all prior outputs and apply `revisions`.

## Examples

Use the example files under `packs/job-application-agent/examples/`:
- `examples/run1_input.md`
- `examples/run1_output.md`
- `examples/run2_input.md`
- `examples/run2_output.md`

Each example should include inputs and all intermediate outputs for reproducibility.

## Evidence

- `benchmark/benchmark_table.md`
- `tutorial/tutorial_writeup.md`
