# Feature 07: Repository/Service Topology and Location Index

## Problem

Maintenance work depends on knowing exactly where each service/library lives and how to build/test it in isolation. ADRs may state isolation principles, but without a maintained location index planning remains slow and error-prone.

## Goal

Provide a canonical topology/index artifact that maps services and libraries to repositories (or monorepo roots), with isolated build/test entrypoints.

## Feature description

Introduce a repository topology index that answers for each service/library:

- where code is located
- who owns it
- how to build/test it independently
- what docs/runbooks govern it

Minimum fields per entry:

- `asset_id` (service/library)
- `asset_type`
- `repo_name`
- `repo_url`
- `repo_root_or_subroot`
- `owner_team`
- `build_command`
- `test_command`
- `runtime/deploy_reference`
- `linked_architecture_ids`
- `linked_runbook_paths`
- `status` (`ACTIVE`, `DEPRECATED`, `MIGRATING`)

## User stories

1. As a maintainer, I can immediately find where a service/library is implemented and test it in isolation.
2. As a planner, I can estimate change impact by traversing repo and ownership boundaries.
3. As a release reviewer, I can verify that each changed service has a known location and test path.

## Workflow integration

- Architect phase references intended topology for new/changed assets.
- Developer phase updates topology when assets move/split/new repos are created.
- Maintenance phase uses topology index as primary source for impact targeting.
- Release gate checks topology index freshness for all changed assets.

## Acceptance criteria

- Every active service/library has a topology index entry.
- Each entry includes isolated build/test commands.
- Changed assets in a release cannot pass if topology index is stale/missing.

## Artifacts to add/update (proposed)

- `docs/operations/repo-service-topology.md`
- `docs/artifacts/repo-service-topology.yaml`
- `docs/artifacts/changed-asset-topology-check.yaml`

## Open questions

- Should topology be centralized in one repo or federated with periodic aggregation?
- How should monorepo subroot moves be versioned and audited?
- Should ownership validation integrate with org/team directories automatically?
