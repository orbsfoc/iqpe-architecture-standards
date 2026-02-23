---
doc_id: DOC-03-services-service-catalog
title: Service Catalog
doc_type: service-description
concern: service
status: accepted
phase_scope:
- MVP
- Pilot
- Production
- Scale
owner_role: service_owner
accountable_role: principal_architect
reviewers:
- tech_lead
- sre_lead
tags:
- ai-development
- service
- traceability
linked_ids:
- SVC-BILLING-01
- SVC-BOOTSTRAP-01
- SVC-CURRICULUM-01
- SVC-EXPERIENCE-01
- SVC-IDENTITY-01
- SVC-ORG-01
- SVC-PROGRESS-01
review_cadence: monthly
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# Service Catalog

## Service Candidates
- SVC-IDENTITY-01: Authentication and Session Service
- SVC-BOOTSTRAP-01: Frontend Bootstrap Configuration Service
- SVC-CURRICULUM-01: Curriculum Content and Structure Service
- SVC-EXPERIENCE-01: Learning Experience Orchestration Service
- SVC-PROGRESS-01: Progression and Mastery Service
- SVC-ORG-01: Organisation Hierarchy and Roles Service
- SVC-BILLING-01: Billing and Subscription Service

## Service Metadata Requirements
- Owner role
- Phase scope
- Interface contracts (OpenAPI/event schemas)
- SLO targets
- Dependencies and shared platform capabilities

## Shared Platform Services
- Authentication/session primitives
- Theme/config provider
- Observability and policy enforcement primitives

## Baseline Implementation Guides
- Go + PostgreSQL access: `04-components/implementation-guides/golang-postgres-access-guide.md`
- Go + Redis 7 access: `04-components/implementation-guides/golang-redis7-access-guide.md`
- Redis 7 modules: `04-components/implementation-guides/redis7-modules-guide.md`
- OpenAPI code generation: `04-components/implementation-guides/openapi-codegen-guide.md`
- Service linkage map: `04-components/implementation-guides/service-implementation-linkage.md`
