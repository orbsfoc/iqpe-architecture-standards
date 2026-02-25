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
- `storage.strategy_required`: require explicit storage strategy by data category.
- `storage.primary_system_of_record`: preferred primary source-of-truth storage model.
- `storage.cache_policy_required`: require cache invalidation + TTL strategy.
- `storage.object_storage_for_blobs_required`: require blob/binary payloads to use object storage.
- `eventing.async_eventing_policy`: define when asynchronous eventing is required vs optional.
- `eventing.delivery_semantics_default`: default delivery semantics (for example at-least-once).
- `eventing.ordering_scope_default`: required ordering scope (for example per aggregate key).
- `eventing.schema_versioning_required`: require versioned event contracts.
- `eventing.idempotent_consumers_required`: require idempotent event consumers.
- `production.scalability_budget_required`: require throughput/scale budget at planning time.
- `production.performance_slo_required`: require explicit latency/error SLO targets.
- `production.maintainability_controls_required`: require maintainability controls (ownership, runbooks, tests).
- `production.upgrade_strategy_required`: require backward-compatible upgrade path and rollback plan.
- `production.zero_downtime_upgrades_required`: require upgrade plans that avoid planned downtime for production traffic.
- `production.operability_slos_required`: require observability and operational SLO plans.

## Minimum planning artifacts
- `docs/repo-topology-decision.md`
- `docs/openapi-contract-plan.md` (when HTTP boundaries exist)
- `docs/planning-behavior-resolution.md`
- `docs/plans/index.md`
- `docs/plans/PLAN-*.md` (when `plan_storage_mode=per-story-files`)
- `docs/dependency-graph.md` or equivalent machine-readable graph
- `docs/plans/storage-planning-behavior.md`
- `docs/plans/eventing-planning-behavior.md`
- `docs/plans/production-capability-planning-behavior.md`

## Gate behavior
- If profile is missing or not loaded via MCP evidence, planning status is `BLOCKED`.
- If required controls are unresolved or violated, implementation status is `BLOCKED`.
- If zero-downtime upgrade strategy is missing for production-facing changes, planning status is `BLOCKED`.

For HTTP/API implementation work, if mandatory contract-first controls are unset, status must default to `BLOCKED` until controls are resolved.

## Dependency sequencing examples
- Example A (API-first): OpenAPI spec approved -> server stub generation -> client SDK/typed client -> feature implementation -> contract tests.
- Example B (UI depends on API): OpenAPI approved -> API handler implementation -> UI integration -> end-to-end tests.
- Example C (error schema): Error schema fixed in OpenAPI -> server enforcement -> client error handling -> negative-path tests.
