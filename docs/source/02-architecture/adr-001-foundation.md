---
doc_id: ADR-POC-001
title: ADR-POC-001 Session and Theme POC Foundation
doc_type: decision
concern: architecture
status: accepted
phase_scope:
- MVP
owner_role: principal_architect
accountable_role: platform_lead
reviewers:
- tech_lead
- service_owner
tags:
- ai-development
- adr
- poc
linked_ids:
- FEAT-POC-001
- SVC-SESSION-01
- SVC-THEME-01
- ADR-POC-002
review_cadence: monthly
source_of_truth: true
version: '1.0'
specificity: platform-shared
---

# ADR-POC-001 Session and Theme POC Foundation

## Decision
Use split services for session and theme concerns with one lightweight frontend page.

## Consequences
- Enables independent service evolution.
- Keeps the POC architecture aligned with future production decomposition.
- Technical stack decisions can be auto-approved when backed by `ADR-POC-002`.
