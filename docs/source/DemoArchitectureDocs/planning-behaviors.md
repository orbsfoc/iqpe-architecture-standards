# Planning Behaviors Policy (MCP-Configurable)

## Purpose
Define a generic, dependency-driven planning behavior model that can be configured per run via machine-readable profile data and consumed through MCP tooling.

## Policy outcomes
- Planning is split into explicit workstreams.
- Dependencies between workstreams are identified and gated.
- Contract-first interface decisions are resolved before dependent implementation.
- Review and feedback loops are mandatory across code and integration phases.

## MCP configurability model
- Source of truth profile: `planning-behavior-profile.yaml`
- Planning phase must load profile via MCP file/tool access and record effective settings.
- Effective settings must be written to `docs/planning-behavior-resolution.md` in the target project.

## Required behavior controls
- `topology.default`: baseline topology strategy.
- `topology.service_per_repo_best_practice`: whether service-per-repo is default best-practice.
- `contracts.require_openapi_for_http`: enforce OpenAPI for HTTP boundaries.
- `plan_storage_mode`: planning artifact storage mode (for example `single-file`, `per-story-files`).
- `plan_directory`: required location for plan artifacts.
- `plan_index_file`: index file that maps requirements/workstreams to plan artifacts.
- `plan_story_file_pattern`: required naming pattern for per-story plans.
- `plan_traceability_required`: enforce per-story traceability mapping (`REQ -> PLAN -> DIAG -> TEST/DEF`).
- `workstreams.require_dependency_graph`: require dependency graph artifact.
- `reviews.require_code_review_feedback_loop`: require reviewer feedback + developer remediation loop.
- `reviews.require_coding_principles`: required coding principles (for example SOLID, DRY).
- `integration.require_gate_after_prerequisites`: integration/orchestration can start only after prerequisites pass.
- `evidence.require_ai_usage_metrics`: require request/token/cost recording when telemetry is available.

## Minimum planning artifacts
- `docs/repo-topology-decision.md`
- `docs/openapi-contract-plan.md` (when HTTP boundaries exist)
- `docs/planning-behavior-resolution.md`
- `docs/plans/index.md`
- `docs/plans/PLAN-*.md` (when `plan_storage_mode=per-story-files`)
- `docs/dependency-graph.md` or equivalent machine-readable graph

## Gate behavior
- If profile is missing or not loaded via MCP evidence, planning status is `BLOCKED`.
- If required controls are unresolved or violated, implementation status is `BLOCKED`.

For HTTP/API implementation work, if mandatory contract-first controls are unset, status must default to `BLOCKED` until controls are resolved.

## Dependency sequencing examples
- Example A (API-first): OpenAPI spec approved -> server stub generation -> client SDK/typed client -> feature implementation -> contract tests.
- Example B (UI depends on API): OpenAPI approved -> API handler implementation -> UI integration -> end-to-end tests.
- Example C (error schema): Error schema fixed in OpenAPI -> server enforcement -> client error handling -> negative-path tests.
