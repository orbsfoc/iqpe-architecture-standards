# Feature 09: Traceability Metadata Schema and Human-Readable Overviews

## Problem

Traceability requires consistent metadata at the code unit level, but current workflows do not define a standard metadata schema across services/libraries/components.

At the same time, teams need human-readable overviews (system/product/architecture/operations) generated from the same data backbone.

## Goal

Standardize per-unit metadata and define overview data products that can be generated deterministically for humans.

## Feature description

### A) Code-unit metadata schema (minimum)

Apply metadata to each maintainable unit (service, library, module, component):

- `unit_id`
- `unit_type`
- `repo_name`
- `repo_path`
- `owner_team`
- `domain`
- `linked_req_ids`
- `linked_plan_ids`
- `linked_adr_ids`
- `linked_tc_ids`
- `linked_test_ids`
- `build_command`
- `test_command`
- `deploy_reference`
- `status` (`ACTIVE`, `DEPRECATED`, `MIGRATING`)
- `last_reviewed_at`

### B) Human-readable overview products

Generate/update the following overview views:

1. **System Overview**
   - service/library topology
   - integration boundaries
2. **Product Overview**
   - capability to service/library mapping
   - requirement coverage summary
3. **Architecture Overview**
   - ADR and technology-policy decisions
   - phase suitability and exceptions
4. **Operations Overview**
   - build/test/deploy readiness
   - runbook and ownership coverage

### C) Data collection pipeline

Collect from:

- local repo metadata files
- MCP outputs (policy, preflight, tech-detect, validation)
- traceability matrix and gate artifacts

Produce:

- machine-readable aggregate (`yaml/json`)
- human-readable markdown summaries

## User stories

1. As a maintainer, I can find all docs/tests/owners linked to a changed unit.
2. As a product lead, I can view requirement coverage and implementation status by capability.
3. As a release reviewer, I can validate architecture and operations readiness from generated summaries.

## Workflow integration

- Developer/Maintenance phases must update unit metadata for changed units.
- Release phase must regenerate overview summaries and verify consistency checks.
- Missing metadata for changed units causes `BLOCKED`.

## Acceptance criteria

- Changed units always include required metadata fields.
- Overview artifacts regenerate deterministically from source metadata.
- Overview inconsistencies are surfaced before release approval.

## Artifacts to add/update (proposed)

- `docs/artifacts/unit-metadata-index.yaml`
- `docs/system-overview.md`
- `docs/product-overview.md`
- `docs/architecture-overview.md`
- `docs/operations-overview.md`
- `docs/artifacts/overview-consistency-report.yaml`

## Open questions

- Should metadata live next to code in each repo or in a central index only?
- How should schema evolution be versioned?
- Which overview sections are mandatory for every release vs major releases only?
