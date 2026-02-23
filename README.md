# iqpe-architecture-standards

Repository for architecture decisions, phase-aware technology policy, and tech radar governance standards.

## Extracted package contents

- `docs/source/DemoArchitectureDocs` (merged architecture source set)
- `docs/source/02-architecture` (concrete architecture baseline)
- `docs/README.md` (architecture standards docs index)

## Owns

- ADR baseline and decision policy
- Phase/environment technology policy matrix
- Tech radar standards and release expectations
- Architecture-to-operations linkage standards

## Required standards

- All policy changes require authority metadata.
- Keep policy matrix machine-readable and human-readable.
- Maintain changelog with impacted policy IDs.

## CI and hosting

- GitHub Actions is the active CI host for early testing.
- Policy quality checks should remain portable as command contracts.
- Follow `CI-HOSTING-PORTABILITY.md` in this repo after extraction.

## Extraction provenance

- See `EXTRACTION-MANIFEST.md` for source mapping from monorepo paths.
