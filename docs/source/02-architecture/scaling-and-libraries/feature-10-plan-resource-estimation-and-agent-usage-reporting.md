# Feature 10: Plan Resource Estimation and Developer-Agent Usage Reporting

## Problem

Plans currently capture scope and sequencing, but they do not consistently estimate expected token/request consumption. Developer-agent sessions also lack a deterministic post-run report of actual requests and token spend.

Without this, teams cannot:

- forecast LLM/tool cost and throughput per plan
- compare estimated vs actual execution cost
- optimize orchestration strategy (sequence vs concurrent) using evidence

## Goal

Require resource budgeting at plan time and resource accountability at developer-agent execution time.

## Feature description

Introduce two mandatory artifacts:

1. **Plan Resource Estimation Artifact** (pre-execution)
2. **Developer-Agent Usage Report Artifact** (post-execution)

### A) Plan estimation (minimum fields)

Per plan and slice:

- `plan_id`
- `slice_id` (or `FULL_PLAN` when not sliced)
- `estimated_requests`
- `estimated_prompt_tokens`
- `estimated_completion_tokens`
- `estimation_method` (`HISTORICAL`, `HEURISTIC`, `MANUAL`)
- `estimation_owner`
- `estimation_timestamp`

### B) Developer-agent usage report (minimum fields)

Per developer-agent execution:

- `run_id`
- `plan_id`
- `slice_id`
- `agent_id`
- `actual_requests`
- `actual_prompt_tokens`
- `actual_completion_tokens`
- `actual_total_tokens`
- `duration_seconds`
- `status` (`PASS`, `FAIL`, `BLOCKED`)
- `report_timestamp`

### C) Variance and governance summary

Compute and persist:

- request variance (`actual_requests - estimated_requests`)
- token variance (`actual_total_tokens - estimated_total_tokens`)
- variance ratio
- threshold breach flags

## User stories

1. As a planner, I can estimate token/request budget before plan approval.
2. As a developer lead, I can compare estimated vs actual spend by plan slice.
3. As a release reviewer, I can verify all developer-agent runs produced usage reports.
4. As a maintainer, I can tune orchestration and budgets from historical variance data.

## Workflow integration

- Planning gate requires estimation artifact for each approved plan/slice.
- Developer gate requires usage report for each developer-agent run.
- Release gate checks that all changed plan slices have both estimation and actual report coverage.

## Acceptance criteria

- No plan enters `ready-for-build` without estimation coverage.
- Every developer-agent run writes a usage report.
- Release gate fails if report coverage is incomplete.
- Variance summary is generated and linked in release evidence.

## Artifacts to add/update (proposed)

- `docs/artifacts/plan-resource-estimation.yaml`
- `docs/artifacts/developer-agent-usage-report.yaml`
- `docs/artifacts/resource-variance-summary.yaml`

## Open questions

- Should thresholds be global or phase-specific?
- Should token budget policy differ by environment (POC/MVP/PROD)?
- Should per-agent usage include tool-call breakdown beyond request/token totals?
