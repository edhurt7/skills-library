# Tutorial Writeup (HW2 Style)

## Objective

Define and document a reusable, multi-step Job Application Agent that converts a job description and candidate experience into tailored, compliant resume bullets and a cover letter with explicit gap handling.

## Background

This pack operationalizes a four-skill workflow that separates extraction, mapping, writing, and compliance review to reduce hallucinations and improve traceability.

## 1) Workflow Overview (what the system does end-to-end)

The system ingests a job description and candidate experience, extracts a role specification, maps evidence to requirements, generates application materials, and performs compliance review before finalizing outputs.

## 2) System Components + Orchestration (4 skills, what each does, flow)

- `packs/job-application-agent/skills/01_jd-extractor.md`: Converts a job description into a structured `role_spec`.
- `packs/job-application-agent/skills/02_experience-mapper.md`: Maps candidate evidence to requirements and produces `mapping`, `gaps`, `do_not_claim`.
- `packs/job-application-agent/skills/03_writer.md`: Produces `resume_bullets`, `cover_letter`, and `keyword_report`.
- `packs/job-application-agent/skills/04_critic-compliance.md`: Reviews outputs, issues findings, and produces revisions and a scorecard.

Flow: JD Extractor → Experience Mapper → Writer → Critic/Compliance.

## 3) Setup + How to Run (exact steps a classmate can follow)

1. Open `packs/job-application-agent/examples/run1_input.md` and paste a job description and candidate experience.
2. Run Skills 01–04 in order: paste the job description into Skill 01 to produce `role_spec`; paste `role_spec` plus candidate experience into Skill 02 to produce `mapping`, `gaps`, and `do_not_claim`; paste `role_spec` + `mapping` + `gaps` + `do_not_claim` into Skill 03 to produce `resume_bullets`, `cover_letter`, `keyword_report`; paste all prior outputs into Skill 04 to produce `issues_found`, `revisions`, and `scorecard`, and capture each artifact as you go.
3. Save outputs to `packs/job-application-agent/examples/run1_output.md`.
4. Repeat for Run 2 using `packs/job-application-agent/examples/run2_input.md` and save to `packs/job-application-agent/examples/run2_output.md`.
5. Update `packs/job-application-agent/benchmark/benchmark_table.md` with the two runs.

Repro Steps (checklist):

- [ ] Paste inputs into `packs/job-application-agent/examples/run1_input.md`
- [ ] Execute Skills 01–04 in order
- [ ] Save outputs to `packs/job-application-agent/examples/run1_output.md`
- [ ] Paste inputs into `packs/job-application-agent/examples/run2_input.md`
- [ ] Execute Skills 01–04 in order
- [ ] Save outputs to `packs/job-application-agent/examples/run2_output.md`
- [ ] Update `packs/job-application-agent/benchmark/benchmark_table.md`

## 4) Evidence: Two Runs (link to example files and summarize what happened)

- Run 1: `packs/job-application-agent/examples/run1_output.md` — honest outputs with clear domain gaps; alignment limited by missing networking specifics.
- Run 2: `packs/job-application-agent/examples/run2_output.md` — improved TPM framing and keyword coverage while keeping domain gaps explicit.

## Tasks

1. Extract a structured role specification from a job description.
2. Map candidate evidence to role requirements, capturing gaps and non-claims.
3. Generate compliant application materials and apply a critique pass.

## Requirements

- Deliverables: `role_spec`, `mapping`, `gaps`, `do_not_claim`, `resume_bullets`, `cover_letter`, `keyword_report`, critique outputs.
- Constraints: no fabricated tools/credentials/metrics; label assumptions; outputs must be paste-ready for downstream steps.

## Grading Rubric

| Criterion | Points | Description |
| --- | --- | --- |
| Correctness |  | _Meets required outputs and behaviors._ |
| Completeness |  | _Covers all tasks and edge cases._ |
| Clarity |  | _Clear explanations, organization, and formatting._ |
| Reproducibility |  | _Steps are repeatable; environment captured._ |
| Efficiency |  | _Reasonable performance and resource use._ |
| Total |  |  |

## Submission

Submit the following artifacts:

- `packs/job-application-agent/examples/run1_output.md`
- `packs/job-application-agent/examples/run2_output.md`
- `packs/job-application-agent/benchmark/benchmark_table.md`

## Iteration

### Run 1 Evidence (Problem)

- Gaps observed: IP procurement/allocation strategy, IPv6 planning/migration, routing/subnetting/topology, cloud networking, dashboards/KPIs, tooling requirements, and architecture planning.
- Missing keywords in Run 1: IP procurement, IP allocation, IPv6 migration, full mesh connectivity, subnetting, routing, network topology, dashboards, KPIs, cost tracking, platform tooling requirements, Azure networking, AIOps.
- Alignment score in Run 1 scorecard: alignment_to_role = 6.

### Changes Applied to `packs/job-application-agent/skills/03_writer.md`

- Added a Transferable TPM Framing rule requiring every resume bullet to map to TPM mechanics: governance, dependency management, milestone execution, risk management, stakeholder alignment, reporting cadence, action tracking.
- Added a gap-bridging paragraph requirement in the cover letter: acknowledge 2–3 key gaps and describe a concrete approach (partner with SMEs, structured learning plan, ask clarifying questions, document decisions, create dashboards).
- Added a keyword rule requiring at least 8 supportable role keywords; domain keywords (routing/subnetting/IPv6) allowed only if explicitly labeled as learning areas.

### Before/After (Run 2)

- Before (Run 1): keyword usage was sparse and skewed toward incident response; TPM mechanics were implicit rather than explicit.
- After (Run 2): keyword count reached 9 supportable TPM keywords and each bullet explicitly mapped to TPM mechanics, improving alignment without introducing unsupported domain claims.

Step 14 change summary: the Writer rules were updated to enforce TPM mechanic mapping, add a gap-bridging paragraph, and require a minimum of 8 supportable role keywords.

## 5) Iteration Summary

See the detailed Iteration section above for Run 1 evidence and the exact changes to `packs/job-application-agent/skills/03_writer.md`. In summary, the Step 14 updates improved TPM framing and keyword density in Run 2 without adding unsupported domain claims.

## 6) Mini-Benchmark (cases, baseline, metrics, results, worst failure)

Benchmark table: `packs/job-application-agent/benchmark/benchmark_table.md`.

- Baseline: single prompt "write bullets and cover letter".
- Metrics: Relevance, Truthfulness, Clarity, ATS Alignment (1–5).
- Results: Run 2 (Revised) scored higher on ATS Alignment than Run 1, while Truthfulness remained high.
- Example comparison: Agent Run 2 ATS Alignment 3/5 vs baseline single-prompt ATS Alignment TBD/5 (fill from `packs/job-application-agent/benchmark/benchmark_table.md`).
- Worst failure: domain misalignment for networking-heavy roles when experience lacks deployment or engineering evidence.

## 7) Reflection / Limitations / Next Improvements

Limitations include weak domain alignment when networking-specific experience is absent and reliance on transferable framing. Next improvements: add a structured “learning plan” output field, expand the Mapper to classify partial evidence by level, and introduce a lightweight domain glossary to better anchor keyword choices.

## References

Artifact paths:

- Skills: `packs/job-application-agent/skills/01_jd-extractor.md`, `packs/job-application-agent/skills/02_experience-mapper.md`, `packs/job-application-agent/skills/03_writer.md`, `packs/job-application-agent/skills/04_critic-compliance.md`
- Examples: `packs/job-application-agent/examples/run1_output.md`, `packs/job-application-agent/examples/run2_output.md`
- Benchmark: `packs/job-application-agent/benchmark/benchmark_table.md`
