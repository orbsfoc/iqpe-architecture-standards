---
doc_id: ADR-002
title: 'ADR-002: OpenAPI Contract-First APIs'
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
- ADR-002
- SVC-BOOTSTRAP-01
- SVC-EXPERIENCE-01
- SVC-IDENTITY-01
- SVC-PROGRESS-01
review_cadence: change-driven
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# ADR-002: OpenAPI Contract-First APIs

## Status
Accepted

## Context
Service and interface docs specify explicit API contracts and stable response semantics for frontend and inter-service integration.

## Decision
Define and version OpenAPI contracts before implementation; generated and manual clients must align with those specs.

## Linked Requirements
- MVP-CORE-002
- MVP-CORE-042
- MVP-CORE-043

## Linked Services
- SVC-BOOTSTRAP-01
- SVC-IDENTITY-01
- SVC-EXPERIENCE-01
- SVC-PROGRESS-01

## Provided Functions
- Contract-governed endpoint definitions
- Standard error structure and status handling
- Versioned API path policy

## Required Functions/Dependencies
- OpenAPI validation in CI
- Backward-compatibility checks at phase boundaries
- Change linkage to ADR and phase model

## Implemented Technical Specs
- Bootstrap API specification
- KU-to-Experience request/response contract
- Achievement-to-Visual contract schema

## Source Documents
- SampleProductDocs/MVP-Design/Core-Requirements.md
- SampleProductDocs/Design/Interface-Spec-Bootstrap-API.md
- SampleProductDocs/Design/Interface-Spec-KU-to-Experience.md
- SampleProductDocs/Design/Interface-Spec-Achievement-to-Visual.md
