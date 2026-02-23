---
doc_id: ADR-POC-002
title: ADR-POC-002 Approved Technology Baseline and Integration Policy
doc_type: decision
concern: architecture
status: accepted
phase_scope:
- MVP
owner_role: principal_architect
accountable_role: platform_lead
reviewers:
- tech_lead
- service_owner
tags:
- ai-development
- adr
- approved-tech
linked_ids:
- ADR-POC-001
- ARCH-POC-001
review_cadence: monthly
source_of_truth: true
version: '1.1'
specificity: platform-shared
---

# ADR-POC-002 Approved Technology Baseline and Integration Policy

## Decision
Adopt the following approved technology baseline for POC and MVP delivery:

- Backend runtime: Go 1.21+
- Primary persistence: PostgreSQL 15+
- Cache/session store: Redis 7.4
- API contract format: OpenAPI 3.1
- Container runtime/build: Docker (permitted)
- Local orchestration for developer environments: Docker Compose (permitted for POC and MVP local implementations only)

## Container and local orchestration guide
1. Docker usage
   - Use Docker images for reproducible build and runtime parity across local/CI environments.
   - Keep Dockerfiles service-specific and minimal, with pinned base image versions.

2. Docker Compose scope restriction
   - Docker Compose is restricted to POC and MVP local implementation workflows.
   - Docker Compose must not be the production orchestration standard.

3. Production handoff expectation
   - Production deployment manifests must be promoted to platform-approved orchestration patterns.
   - Any production use of Docker Compose requires explicit architecture exception approval.

## Service repository and directory-root best practice
- Each service should live in its own repository where possible.
- If a monorepo is used, each service must have its own top-level directory root with isolated build/test/runtime assets.
- Shared libraries must be versioned and consumed via explicit contracts; avoid implicit cross-service internal imports.

## Authority
- Authoritative Source: Corporate architecture technology baseline + platform ADR governance
- Approval Owner: platform_lead
- Approval Status: APPROVED

## Go integration policy
All service and adapter integrations in Go must follow these patterns:

1. Hexagonal boundaries
   - Keep domain logic free of transport/storage concerns.
   - Integrations must be implemented behind ports/interfaces.

2. Adapter isolation
   - One adapter per external dependency (DB, Redis, HTTP upstream, queue).
   - No direct external client calls from domain layer.

3. Context and timeout discipline
   - Every integration call accepts `context.Context`.
   - Apply explicit timeouts and cancellation propagation.

4. Resilience and observability
   - Implement retries only at adapter boundary with bounded backoff.
   - Emit structured logs, metrics, and correlation IDs for integration paths.

5. Contract-first integration
   - External API adapters must align to OpenAPI contracts.
   - Data mapping/validation happens at adapter edge, not in domain core.

## Consequences
- Teams can auto-approve technical decisions that reference this ADR.
- Any local integration/adaptor choice outside this baseline remains `PROPOSED` or `BLOCKED` until corporate approval.
