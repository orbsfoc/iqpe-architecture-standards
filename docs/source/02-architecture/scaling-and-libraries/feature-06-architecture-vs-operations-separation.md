# Feature 06: Architecture vs Operations Separation

## Problem

Architecture decisions and operational implementation details are often mixed in the same artifacts, which makes planning and maintenance harder to reason about.

This creates confusion in questions like:

- What must be true by design (architecture intent)?
- How exactly is it deployed, run, monitored, and recovered (operations reality)?

## Goal

Introduce a clear separation between architecture artifacts and operations artifacts while preserving linkage between them.

## Feature description

Define two explicit artifact lanes:

1. **Architecture lane**
   - service boundaries
   - integration contracts
   - ADR decisions
   - technology constraints and policy rationale

2. **Operations lane**
   - repository locations
   - build/test pipelines and entrypoints
   - deployment/runtime topology
   - runbooks, observability, and incident procedures

Require explicit cross-linking from architecture IDs to operations IDs.

## User stories

1. As an architect, I can evolve ADR and service boundaries without polluting docs with environment-specific run details.
2. As an operations owner, I can find concrete runtime/build/test implementation details without reading every ADR.
3. As a maintainer, I can trace from architecture decision to repo and runbook quickly.

## Workflow integration

- Architect phase outputs architecture lane artifacts.
- Developer and maintenance phases update operations lane artifacts.
- Release phase verifies linkage completeness between lanes.

## Acceptance criteria

- Architecture artifacts do not contain operational runbook clutter.
- Operations artifacts provide concrete implementation details (repo, build, test, deploy, runbook).
- Each critical architecture decision has at least one linked operational implementation reference.

## Artifacts to add/update (proposed)

- `docs/architecture/` (ADRs, constraints, service model)
- `docs/operations/` (repo topology, build/test maps, runbooks)
- `docs/artifacts/architecture-operations-link-map.yaml`

## Open questions

- Should link-map completeness be an Architect gate or Release gate requirement?
- Which lane owns environment-specific policy exceptions?
- How should ownership be split across architecture and operations teams?
