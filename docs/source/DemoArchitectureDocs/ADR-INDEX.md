---
doc_id: DEC-ADR-INDEX-001
title: ADR Index
doc_type: index
concern: architecture
status: accepted
phase_scope:
- MVP
- Pilot
- Production
- Scale
owner_role: principal_architect
accountable_role: head_of_engineering
reviewers:
- tech_lead
tags:
- ai-development
- architecture
- index
- traceability
linked_ids:
- ADR-001
- ADR-002
- ADR-003
- ADR-004
- ADR-005
- ADR-006
- ADR-007
- ADR-008
- ADR-009
review_cadence: monthly
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# ADR Index

## Purpose
Central index for architectural decisions and links to requirements, services, and phase impacts.

## Extracted ADR Set
- ADR-001: Hexagonal architecture for Go services.
- ADR-002: OpenAPI contract-first APIs.
- ADR-003: Tiered authentication with MVP session baseline.
- ADR-004: Bootstrap aggregation pattern for frontend initialization.
- ADR-005: Event-driven achievement and visualization pipeline.
- ADR-006: KU-to-Experience versioned contract.
- ADR-007: Audience-safe achievement data views.
- ADR-008: Edge security and platform controls.
- ADR-009: Go implementation and DI standards.

## ADR Documents
- `02-decisions/adr/ADR-001-hexagonal-architecture.md`
- `02-decisions/adr/ADR-002-openapi-contract-first.md`
- `02-decisions/adr/ADR-003-tiered-authentication-evolution.md`
- `02-decisions/adr/ADR-004-bootstrap-aggregation.md`
- `02-decisions/adr/ADR-005-event-driven-achievement-pipeline.md`
- `02-decisions/adr/ADR-006-ku-to-experience-contract.md`
- `02-decisions/adr/ADR-007-audience-safe-achievement-views.md`
- `02-decisions/adr/ADR-008-edge-security-and-platform-controls.md`
- `02-decisions/adr/ADR-009-go-implementation-standards.md`

## Link Registries
- `03-services/service-function-link-matrix.md`
- `04-components/component-spec-implementation-map.md`
- `artifacts/adr-links.yaml`
- `artifacts/service-tech-implementation-links.yaml`

## Linking Rules
- Every ADR links to at least one requirement/feature.
- Every service contract change links to one ADR.
- Every superseded requirement references replacement ADR/REQ IDs.
