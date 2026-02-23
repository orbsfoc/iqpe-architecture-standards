---
doc_id: ADR-007
title: 'ADR-007: Audience-Safe Achievement Data Views'
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
- ADR-007
- REQ-ARCH-002
- SVC-ORG-01
- SVC-PROGRESS-01
review_cadence: change-driven
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# ADR-007: Audience-Safe Achievement Data Views

## Status
Accepted

## Context
Achievement payloads include learner, educator, and analytics perspectives with different safety and privacy needs.

## Decision
Standardize achievement payload separation by audience to enforce safe learner UX and richer educator/analytics visibility.

## Linked Requirements
- REQ-ARCH-002

## Linked Services
- SVC-PROGRESS-01
- SVC-ORG-01

## Provided Functions
- Learner-safe progress messaging
- Educator intervention signals
- Analytics diagnostic detail

## Required Functions/Dependencies
- Audience-based filtering policy
- Permission checks by role and hierarchy
- Data minimization for learner-facing responses

## Implemented Technical Specs
- Achievement data model with `learnerView`, `educatorView`, `analyticsView`
- Role-sensitive visual rendering controls

## Source Documents
- SampleProductDocs/Design/Interface-Spec-Achievement-to-Visual.md
- SampleProductDocs/Design/System-Architecture.md
