---
doc_id: ADR-006
title: 'ADR-006: Knowledge Unit to Experience Contract'
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
- ADR-006
- REQ-ARCH-007
- SVC-CURRICULUM-01
- SVC-EXPERIENCE-01
review_cadence: change-driven
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# ADR-006: Knowledge Unit to Experience Contract

## Status
Accepted

## Context
Learning Data and Experience services require stable KU metadata contracts including Bloom levels, prerequisites, and method context.

## Decision
Define a versioned KU-to-Experience contract as the authoritative integration interface for generating learning activities.

## Linked Requirements
- REQ-ARCH-007

## Linked Services
- SVC-CURRICULUM-01
- SVC-EXPERIENCE-01

## Provided Functions
- KU metadata delivery
- Bloom-targeted generation requests
- Method-context aware generation

## Required Functions/Dependencies
- KU graph and prerequisite model
- Learner progression context
- Method applicability mapping

## Implemented Technical Specs
- `POST /api/v1/experiences/generate`
- KU schema with prerequisite and method references

## Source Documents
- SampleProductDocs/Design/Interface-Spec-KU-to-Experience.md
- SampleProductDocs/MVP-Design/Service-Architecture.md
