---
doc_id: DOC-03-services-service-interfaces
title: Service Interface Contracts
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
- IFACE-AUTH-LOGIN-01
- IFACE-AUTH-SESSION-01
- IFACE-BOOTSTRAP-CONFIG-01
- IFACE-PROGRESS-STATE-01
review_cadence: monthly
source_of_truth: true
version: '1.0'
specificity: platform-shared
---



# Service Interface Contracts

## Contract Standards
- REST APIs versioned by path.
- OpenAPI specs as contract source-of-truth.
- Consistent response envelope and error taxonomy.

## Interface Inventory (Initial)
- IFACE-AUTH-LOGIN-01: Learner login/session establish
- IFACE-AUTH-SESSION-01: Session validation/refresh semantics
- IFACE-BOOTSTRAP-CONFIG-01: Public + authenticated bootstrap config
- IFACE-PROGRESS-STATE-01: Learner progress retrieval/update

## Change Control
- Additive changes allowed in-phase.
- Breaking changes only at phase boundaries with migration plan.
- Every interface delta must link to ADR + affected phase.
