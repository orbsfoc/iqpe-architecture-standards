# Architectural Intent ADR Baselines

This directory is the authoritative home for architectural-intent ADR baseline documents consumed by workflow tooling.

## ADR Baselines
- ADR-BEST-PRACTICE-CODE-QUALITY-AND-REVIEW.md
- ADR-GENERAL-DESIGN-PRINCIPLES.md
- ADR-GO-IMPLEMENTATION-STANDARDS.md
- ADR-GO-DESIGN-PRINCIPLES-HEXAGONAL.md
- ADR-GO-PREFERRED-DESIGN-PATTERNS-HEXAGONAL.md
- ADR-DATA-SEPARATION-AND-USAGE-BOUNDARIES.md
- ADR-CQRS-READ-WRITE-MODEL-PATTERNS.md
- ADR-KAFKA-EVENTING-DESIGN-PATTERNS.md

Policy:
- These ADRs are architecture-source artifacts.
- Workflow packs must not ship static ADR payload copies.
- Project runs consume ADR intent via MCP/tooling against approved architecture sources.
