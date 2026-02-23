# Cross-Feature Rollout and Metrics

## Objective

Define a practical rollout path for the scaling + library-governance features and measurable success indicators.

Includes phase-aware technology policy enforcement.

## Rollout phases

### Phase 1: Process-only adoption

- Introduce new planning docs and checklists.
- Require manual completion of:
  - plan slicing table
  - reuse analysis
  - library decision record
  - phase/environment technology policy check
  - architecture vs operations separation map
  - repo/service location index entries for changed assets
  - data classification (local vs MCP vs derived evidence)
  - changed-unit metadata updates and overview refresh notes
  - plan resource estimation (requests/tokens) for each plan/slice
  - developer-agent usage report (actual requests/tokens) for each execution run

### Phase 2: Tool-assisted validation

- Add MCP/tool actions to validate artifact completeness.
- Add deterministic checks in release gate for missing records.
- Add deterministic policy evaluation for phase + environment + technology combinations.
- Add deterministic checks for topology freshness and isolated build/test entrypoints.
- Add deterministic checks for required data classes (local/MCP/evidence) and freshness.
- Add deterministic checks for changed-unit metadata completeness.
- Add deterministic checks for plan estimation artifact completeness.
- Add deterministic checks for developer-agent usage report coverage.

### Phase 3: Automated orchestration

- Add planning orchestrator logic for slicing triggers.
- Add queryable module/library catalog integration.
- Add automatic release blocking for unresolved library approvals.
- Add automated policy matrix evaluation and exception handling workflow.
- Add automated architecture-to-operations linkage validation.
- Add automated changed-asset topology validation before release.
- Add automated data-boundary/freshness validation per gate.
- Add automated generation of human-readable system/product/architecture/operations overviews.
- Add automated estimated-vs-actual token/request variance summaries per plan and release.

## Suggested success metrics

- `% large plans decomposed into slices`
- `% major capabilities with documented reuse search evidence`
- `% new library introductions with approved decision record`
- `% technology decisions with phase-aware policy evaluation`
- `% disallowed technology decisions blocked before release`
- `% changed assets with valid repo/location index records`
- `% changed assets with isolated build/test entrypoints verified`
- `% gate decisions backed by required MCP/local data classes`
- `% changed units with complete metadata records`
- `% releases with regenerated overview artifacts passing consistency checks`
- `% plans with approved request/token estimation before build`
- `% developer-agent runs with complete usage reports`
- `Median request variance per plan (actual vs estimated)`
- `Median token variance per plan (actual vs estimated)`
- `Median lead time reduction for large-scope planning`
- `Reduction in duplicate library/module implementations`

## Guardrails

- Keep governance lightweight for small/simple changes.
- Avoid forcing decomposition where complexity threshold is not met.
- Preserve deterministic PASS/FAIL/BLOCKED gate semantics.

## Dependencies

- Stable MCP action execution and evidence logging.
- Clear ownership for catalog maintenance.
- Agreement on approval owners for library decisions.
- Maintained source-of-truth for repo/service topology and ownership.
- Clear ownership split for architecture artifacts vs operations artifacts.
- Stable metadata schema governance and versioning ownership.
- Agreed freshness policy for MCP-derived and local-derived evidence artifacts.
- Agreed budget policy and variance thresholds for request/token governance.
