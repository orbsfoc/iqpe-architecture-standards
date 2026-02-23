---
doc_id: ADR-003
title: 'ADR-003: Tiered Authentication with MVP Session Baseline'
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
- ADR-003
- SVC-IDENTITY-01
- SVC-ORG-01
review_cadence: change-driven
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# ADR-003: Tiered Authentication with MVP Session Baseline

## Status
Accepted

## Context
MVP focuses on learner session auth; adult OIDC-based auth is intentionally deferred for post-MVP phases.

## Decision
Use secure server-side learner sessions in MVP, then evolve to tiered identity (OIDC/JWT for adult roles) in later phases.

## Linked Requirements
- MVP-CORE-030
- MVP-CORE-031
- MVP-CORE-032
- MVP-AUTH-001 .. MVP-AUTH-043

## Linked Services
- SVC-IDENTITY-01
- SVC-ORG-01

## Provided Functions
- Learner login/logout/session validation
- Sliding session renewal
- Cookie security controls

## Required Functions/Dependencies
- Credential hashing and rate limiting
- Session persistence and expiry cleanup
- Role model extension for adult/org roles

## Implemented Technical Specs
- Session cookie policy (HttpOnly, Secure, SameSite=Strict)
- Session schema and lookup indexes
- Future compatibility path to OIDC/JWT tiers

## Source Documents
- SampleProductDocs/MVP-Design/Authentication.md
- SampleProductDocs/MVP-Design/Core-Requirements.md
- SampleProductDocs/Design/Requirements/01-Identity-Access-Management.md
