# Feature 04: Phase-Aware Technology Policy

## Problem

Current technical decisions are treated as globally valid without considering lifecycle phase (legacy, POC, MVP, production) and environment context (local/demo vs production runtime).

This causes two classes of errors:

1. Over-restricting pragmatic choices in early phases.
2. Allowing non-production-grade choices to pass production gates.

## Goal

Introduce a policy layer where technology decisions are validated against:

- project phase
- workload/environment type
- legacy context

## Feature description

Add a phase-aware decision matrix and gate checks that evaluate whether a tech choice is:

- `ALLOWED`
- `ALLOWED_WITH_CONDITION`
- `DISALLOWED`

Policy evaluation inputs:

- `project_phase` (`LEGACY_SUPPORT`, `POC`, `MVP`, `PILOT`, `PRODUCTION`, `SCALE`)
- `environment` (`LOCAL`, `DEMO`, `NON_PROD`, `PROD`)
- `decision_type` (`RUNTIME`, `ORCHESTRATION`, `LIBRARY`, `FRAMEWORK`, `INFRA`)
- `technology`
- `context_tags` (for example `legacy-java17-estate`)

## Example policy rules

### Java runtime rule

- If `project_phase=LEGACY_SUPPORT` and `context_tags` include `legacy-java17-estate`:
  - `java17` => `ALLOWED`
- If `project_phase` in (`POC`, `MVP`, `PILOT`, `PRODUCTION`, `SCALE`) for new services:
  - `java21` => `ALLOWED`
  - `java17` => `DISALLOWED` unless approved exception exists

### Docker Compose rule

- If `project_phase` in (`POC`, `MVP`) and `environment` in (`LOCAL`, `DEMO`):
  - `docker-compose` => `ALLOWED_WITH_CONDITION`
- If `environment=PROD` or `project_phase` in (`PRODUCTION`, `SCALE`):
  - `docker-compose` => `DISALLOWED`

### Tooling runtime language rule

- For project tooling/runtime utilities (MCP servers, action runners, bootstrap/preflight tooling):
  - `golang` => `ALLOWED`
  - non-Go runtimes => `DISALLOWED` unless approved portability exception exists

## Decision output model (proposed)

Each evaluated decision should produce:

- `decision_id`
- `technology`
- `project_phase`
- `environment`
- `policy_result` (`ALLOWED`, `ALLOWED_WITH_CONDITION`, `DISALLOWED`)
- `conditions_required`
- `exception_required` (`true/false`)
- `authoritative_source`
- `approval_owner`
- `approval_status`

## User stories

1. As an architect, I can choose tech that is valid for the current phase without unnecessary blocking.
2. As a reviewer, I can block decisions that violate production-phase policy.
3. As a maintainer, I can support legacy stacks while steering new development to target baselines.

## Workflow integration

- Architect phase must include phase/environment fields for each major technology decision.
- New-library governance (Feature 03) must call this policy layer before approval.
- Release gate must fail/block when any `DISALLOWED` decision lacks approved exception.

## Acceptance criteria

- Policy checks return deterministic results for phase + environment + technology.
- Legacy-support scenarios can approve Java 17 when explicitly tagged as legacy context.
- New-service scenarios route Java choices to Java 21 baseline.
- Docker Compose is accepted only for local/demo POC/MVP workflows and blocked for production.

## Artifacts to add/update (proposed)

- `docs/technology-policy-matrix.md`
- `docs/artifacts/technology-policy-rules.yaml`
- `docs/artifacts/technology-policy-evaluations.yaml`
- Optional MCP action: `mcp.action.tech_policy_evaluate`

## Open questions

- What exact phase taxonomy should be canonical for all teams?
- Should `ALLOWED_WITH_CONDITION` auto-block until conditions are evidenced, or allow conditional PASS?
- How should exception expiry and revalidation be enforced?
