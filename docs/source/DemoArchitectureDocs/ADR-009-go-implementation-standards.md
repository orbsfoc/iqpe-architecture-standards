---
doc_id: ADR-009
title: 'ADR-009: Go Implementation and Dependency Injection Standards'
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
- ADR-009
- REQ-ARCH-005
- REQ-ARCH-006
- REQ-ARCH-007
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



# ADR-009: Go Implementation and Dependency Injection Standards

## Status
Accepted

## Context
Coding standards require common service layout, constructor-based dependency injection, focused interfaces, and test strategy by layer.

## Decision
All Go services follow the shared project structure and DI conventions defined in architecture/coding standards.

## Linked Requirements
- REQ-ARCH-005
- REQ-ARCH-006
- REQ-ARCH-007

## Linked Services
- SVC-IDENTITY-01
- SVC-CURRICULUM-01
- SVC-EXPERIENCE-01
- SVC-PROGRESS-01
- SVC-BILLING-01

## Provided Functions
- Consistent build/test/deploy ergonomics
- Replaceable adapters and focused ports
- Predictable review and maintenance standards

## Required Functions/Dependencies
- Composition root in `main`
- Interface-based constructor injection
- Layer-scoped automated tests

## Implemented Technical Specs
- Standard folder and package conventions
- Interface segregation limits and adapter boundaries

## Source Documents
- SampleProductDocs/Design/Requirements/22-Architecture-Coding-Standards.md
- SampleProductDocs/Design/Technical-Overview.md
