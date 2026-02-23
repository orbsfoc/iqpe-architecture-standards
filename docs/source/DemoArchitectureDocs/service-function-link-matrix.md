---
doc_id: DOC-03-services-service-function-link-matrix
title: Service Function Link Matrix
doc_type: technical-note
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
- index
- service
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
- CMP-AUTH-01
- CMP-AUTH-02
- CMP-BOOT-01
- CMP-BOOT-02
- CMP-CURR-01
- CMP-PROG-01
- CMP-UI-01
- IFACE-AUTH-LOGIN-01
- IFACE-AUTH-SESSION-01
- IFACE-BOOTSTRAP-CONFIG-01
- IFACE-PROGRESS-STATE-01
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



# Service Function Link Matrix

## Purpose
Link required/provided functions to services, contracts, and implementation components.

| Service ID | Service | Provides Functions | Requires Functions | Primary Contracts | Implemented By Components |
|---|---|---|---|---|---|
| SVC-IDENTITY-01 | Authentication and Session | Login/logout/session validation, preference retrieval | Password hash/rate-limit, session persistence, role checks | IFACE-AUTH-LOGIN-01, IFACE-AUTH-SESSION-01 | CMP-AUTH-01, CMP-AUTH-02 |
| SVC-BOOTSTRAP-01 | Bootstrap Configuration | Unified bootstrap payload, ETag/TTL config response | Feature flags, preference/session state, entitlement lookup | IFACE-BOOTSTRAP-CONFIG-01 | CMP-BOOT-01, CMP-BOOT-02, CMP-UI-01 |
| SVC-CURRICULUM-01 | Curriculum & KU | KU graph, prerequisites, Bloom-level metadata | Curriculum source ingestion, method mapping | KU-to-Experience contract | CMP-CURR-01 |
| SVC-EXPERIENCE-01 | Experience Orchestration | Experience generation and progression orchestration | KU metadata, learner context, question retrieval | KU-to-Experience contract, IFACE-PROGRESS-STATE-01 | CMP-CURR-01, CMP-PROG-01 |
| SVC-PROGRESS-01 | Progression & Mastery | Outcome capture, mastery state, achievement feed | Event bus, persistence, visual rendering pipeline | Achievement-to-Visual contract, IFACE-PROGRESS-STATE-01 | CMP-PROG-01 |
| SVC-ORG-01 | Org Roles & Access | Role-scoped access and reporting views | Identity claims, hierarchy model, policy checks | Role/permission internal contracts | CMP-AUTH-02 |
| SVC-BILLING-01 | Billing & Subscription | Entitlements and subscription state | Payment provider integration, account linkage | Billing internal/API contracts | CMP-BOOT-02 |

## ADR Links
- ADR-001, ADR-002, ADR-003, ADR-004, ADR-005, ADR-006, ADR-007, ADR-008, ADR-009
