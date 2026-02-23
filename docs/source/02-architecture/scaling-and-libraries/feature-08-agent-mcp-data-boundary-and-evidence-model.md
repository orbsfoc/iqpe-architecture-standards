# Feature 08: Agent vs MCP Data Boundary and Evidence Model

## Problem

As feature scope grows, planning quality depends on knowing:

- what data is available locally to the agent
- what data must be fetched from MCP services
- what evidence must be persisted for deterministic review

Without explicit boundaries, workflows become inconsistent and hard to audit.

## Goal

Define a canonical data-boundary model that classifies each data type by source, trust level, freshness policy, and storage location.

## Feature description

Create a data classification matrix with four classes:

1. **Local Workspace Data (Agent-readable)**
   - repository files under scope (`docs/`, source, tests, configs)
   - local generated artifacts already present in repo
2. **MCP-Provided Data (Tool-resolved)**
   - action outputs (`bootstrap`, `preflight`, `tech detect`, template retrieval)
   - policy validations and governance checks
3. **Derived Evidence Data (Persisted)**
   - summaries created from local + MCP inputs
   - gate decisions and traceability reports
4. **External Context Data (Declared input)**
   - `SPEC_DIR`
   - external team/ownership references

Each data item should include metadata:

- `data_id`
- `data_class`
- `source_system`
- `retrieval_method`
- `freshness_sla`
- `trust_level`
- `required_for_gates` (list)
- `storage_path`

## User stories

1. As an architect, I can tell which decisions rely on local evidence vs MCP evidence.
2. As a reviewer, I can audit whether gate decisions used required trusted inputs.
3. As a maintainer, I can re-run only stale data fetches instead of full workflow replay.

## Workflow integration

- Initialization phase builds/updates the data classification matrix.
- Every phase appends evidence references to data IDs used for decisions.
- Release gate fails if required high-trust data classes are missing or stale.

## Acceptance criteria

- Every required gate input maps to a defined data class and source.
- Missing required MCP data is explicitly surfaced as `BLOCKED`.
- Evidence references can be traced from decision -> data ID -> source artifact.

## Artifacts to add/update (proposed)

- `docs/tooling/data-classification-matrix.yaml`
- `docs/tooling/data-freshness-report.yaml`
- `docs/tooling/phase-data-usage-log.md`

## Open questions

- Should stale-data policy differ by phase (POC vs Production)?
- Which data classes are mandatory for each gate?
- Should trust levels be numeric or enum-based?
