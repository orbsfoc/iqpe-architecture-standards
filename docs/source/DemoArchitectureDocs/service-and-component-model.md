---
doc_id: ARCH-POC-001
title: Service and Component Model for Concrete POC
doc_type: architecture
concern: architecture
status: accepted
phase_scope:
- MVP
owner_role: principal_architect
accountable_role: platform_lead
reviewers:
- tech_lead
tags:
- ai-development
- architecture
- poc
linked_ids:
- ADR-POC-001
- ADR-POC-002
- SVC-SESSION-01
- SVC-THEME-01
- CMP-SESSION-API-01
- CMP-THEME-API-01
- CMP-FRONTEND-DASH-01
review_cadence: monthly
source_of_truth: true
version: '1.1'
specificity: platform-shared
---

# Service and Component Model for Concrete POC

## Services
- `SVC-SESSION-01`: session-service (timeout and active session state)
- `SVC-THEME-01`: theme-service (theme preference persistence)

## Components
- `CMP-SESSION-API-01`: REST endpoints for session configuration/state.
- `CMP-THEME-API-01`: REST endpoints for theme configuration.
- `CMP-FRONTEND-DASH-01`: frontend page composing both services.

## Technical section

### Approved technology baseline
- Backend runtime: Go 1.21+
- Primary persistence: PostgreSQL 15+
- Cache/session store: Redis 7.4
- API contracts: OpenAPI 3.1
- Container runtime/build: Docker (permitted)
- Local orchestration for developer environments: Docker Compose (restricted to POC and MVP local implementations)

### Containerization guide
1. Service images
	- Each service should publish its own Docker image with pinned base/runtime versions.
	- Image build should run contract checks and basic health validation.

2. Compose usage boundaries
	- Docker Compose is for local integration and developer workflow in POC/MVP only.
	- Do not treat Compose files as production deployment manifests.

3. Promotion path
	- Before production, services must move to platform-approved orchestration artifacts.
	- Any exception requires architecture review and explicit approval.

### Service repository and root structure best practice
- Prefer one service per repository to keep ownership and release boundaries clear.
- In monorepos, each service must be contained in an independent top-level directory root.
- Keep service-local CI/build/deploy config with each service root; avoid shared implicit coupling.

### Golang integration patterns
1. Port/adapter boundaries
	- Domain services depend on interfaces (ports), not concrete clients.
	- Redis/PostgreSQL/HTTP integrations are implemented as adapters.

2. Context-first calls
	- All integration methods accept `context.Context`.
	- Enforce timeout budgets at adapter entry points.

3. Adapter-specific error mapping
	- Convert infrastructure errors to domain-safe error types at adapter boundary.
	- Preserve correlation IDs for request tracing.

4. Deterministic resilience
	- Use bounded retries only for transient failures.
	- Keep idempotency guarantees for retryable operations.

5. Contract and schema enforcement
	- Validate request/response contracts at integration boundaries.
	- Keep serialization/mapping logic out of domain core.
