---
doc_id: ADR-001
title: 'ADR-001: Hexagonal Architecture for Go Services'
doc_type: adr
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
- service_owner
tags:
- adr
- ai-development
- architecture
- traceability
linked_ids:
- ADR-001
- REQ-ARCH-001
- REQ-ARCH-002
- REQ-ARCH-003
- REQ-ARCH-004
- REQ-ARCH-006
- SVC-BILLING-01
- SVC-CURRICULUM-01
- SVC-EXPERIENCE-01
- SVC-IDENTITY-01
- SVC-PROGRESS-01
review_cadence: change-driven
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# ADR-001: Hexagonal Architecture for Go Services

## Status
Accepted

## Context
Sample docs mandate ports-and-adapters, strict layer boundaries, and inward dependency flow for all Go services.

## Decision
All backend services use Hexagonal Architecture with Domain, Application, and Infrastructure layers.

## Linked Requirements
- REQ-ARCH-001
- REQ-ARCH-002
- REQ-ARCH-003
- REQ-ARCH-004
- REQ-ARCH-006

## Linked Services
- SVC-IDENTITY-01
- SVC-CURRICULUM-01
- SVC-EXPERIENCE-01
- SVC-PROGRESS-01
- SVC-BILLING-01

## Provided Functions
- Stable domain logic independent of adapters
- Swappable infrastructure adapters (Postgres/Redis/MQ/external)
- Layer-specific testing strategy

## Required Functions/Dependencies
- Dependency injection composition root
- Port interfaces in application layer
- Adapter conformance and contract tests

## Implemented Technical Specs
- Standard Go service folder layout (`cmd`, `internal/domain`, `internal/application`, `internal/infrastructure`)
- OpenAPI contract per service

## Source Documents
- SampleProductDocs/Design/Requirements/22-Architecture-Coding-Standards.md
- SampleProductDocs/Design/Technical-Overview.md
