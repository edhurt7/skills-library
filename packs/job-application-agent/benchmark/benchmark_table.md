# Benchmark Table

## Score Summary (1–5)

| Case | Agent (Rel/Truth/Clarity/ATS) | Baseline (Rel/Truth/Clarity/ATS) |
| --- | --- | --- |
| Run 2 (Revised) | 3/4/4/3 | TBD/TBD/TBD/TBD |
| Run 1 (Revised) | 2/4/4/2 | TBD/TBD/TBD/TBD |
| Run 2 (Initial Draft) | 3/4/4/2 | TBD/TBD/TBD/TBD |

Baseline scores will be filled after running the single-prompt baseline for each case.

| Benchmark | Dataset | Baseline | Relevance (1-5) | Truthfulness (1-5) | Clarity (1-5) | ATS Alignment (1-5) | Notes | Worst Failure | Next Fix |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Run 2 (Revised) | Standard case: TPM I Network Deployment Optimization (Google). Uses Run 2 revised outputs. | Single prompt: "write bullets and cover letter" | 3 | 4 | 4 | 3 | Strong TPM mechanics framing; explicit gap-bridging. Domain deployment gaps remain. | Limited domain relevance to network deployment specifics. | Add explicit dependency/milestone plan tied to deployment phases using transferable language without claiming deployment experience. |
| Run 1 (Revised) | Edge case: Networking TPM with deep domain requirements (IP procurement, IPv6, routing). Uses Run 1 revised outputs. | Single prompt: "write bullets and cover letter" | 2 | 4 | 4 | 2 | Honest but low domain alignment; mostly incident-response framing. | Misalignment to networking architecture scope; low keyword coverage. | Add structured learning plan + SME partnership plan and expand TPM mechanics mapping across all bullets. |
| Run 2 (Initial Draft) | Ambiguous case: TPM I Network Deployment with limited direct evidence; uses Run 2 initial draft outputs. | Single prompt: "write bullets and cover letter" | 3 | 4 | 4 | 2 | TPM keywords present but some phrasing could imply ownership of dashboards/timelines. | Possible overreach in KPI/dashboard implication; timeline ownership without evidence. | Tighten language to "reporting artifacts" and clarify coordination vs ownership (as in revised Run 2). |
