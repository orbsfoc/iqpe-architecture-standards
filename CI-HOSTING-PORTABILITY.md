# CI Hosting Portability (Architecture Standards Repo)

## Current host

GitHub Actions is used for early testing.

## Command contract (host-neutral)

Every CI host must preserve these checks:

1. Required baseline docs exist (`README.md`, `CHANGELOG.md`, `OWNERS.md`, `docs/README.md`).
2. Architecture source docs exist (`docs/source/DemoArchitectureDocs/ADR-INDEX.md`, `docs/source/02-architecture/adr-002-approved-tech-baseline.md`).

## Migration rule

When moving away from GitHub, port checks with identical command semantics first, then optimize.
