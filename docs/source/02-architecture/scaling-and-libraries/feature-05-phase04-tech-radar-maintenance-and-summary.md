# Feature 05: Phase 04 Tech Radar Maintenance and Summary

## Problem

Technology decisions evolve during delivery, but the process does not enforce a lightweight, up-to-date technology radar summary at release review time.

Without a Phase 04 checkpoint, teams risk:

- carrying outdated technology assumptions into release decisions
- missing explicit phase suitability context
- weak visibility on which technologies are `adopt`, `trial`, `hold`, or `retire`

## Goal

Make technology radar maintenance and summarization a required Phase 04 (Release Reviewer) activity.

## Feature description

Add mandatory Phase 04 artifacts:

- `docs/tech-radar.md`
- `docs/handoffs/release/tech-radar-summary.md`

The radar should classify each relevant technology by:

- ring/status (`ADOPT`, `TRIAL`, `HOLD`, `RETIRE`)
- phase suitability (`POC`, `MVP`, `PILOT`, `PRODUCTION`, `SCALE`)
- environment suitability (`LOCAL`, `DEMO`, `NON_PROD`, `PROD`)
- rationale and authoritative source
- owner and last review date

## User stories

1. As a release reviewer, I can quickly summarize technology posture before final GO/NO-GO.
2. As an architect, I can maintain a single radar view tied to current policy and implementation choices.
3. As a governance owner, I can detect phase-inappropriate technology choices before release approval.

## Phase 04 workflow integration

During release review:

1. Read current technology decisions and approved constraints.
2. Update `docs/tech-radar.md` with latest ring and suitability.
3. Produce `docs/handoffs/release/tech-radar-summary.md` highlighting:
   - new technologies introduced
   - changed ring decisions
   - any `HOLD/RETIRE` risk affecting release
4. Gate result remains `BLOCKED` if required radar artifacts are missing.

## Acceptance criteria

- Phase 04 cannot pass without both radar artifacts.
- Radar reflects current project-phase policy and release context.
- Summary clearly states release-impacting technology risks and owner actions.

## Artifacts to add/update (proposed)

- `docs/tech-radar.md`
- `docs/handoffs/release/tech-radar-summary.md`
- Optional: `docs/artifacts/tech-radar.json` for deterministic checks

## Open questions

- Should radar updates also be required at Architect phase, with Phase 04 only summarizing deltas?
- Should ring transitions require approval owner sign-off for `PRODUCTION`/`SCALE`?
- What minimum metadata fields should be enforced in automated validation?
