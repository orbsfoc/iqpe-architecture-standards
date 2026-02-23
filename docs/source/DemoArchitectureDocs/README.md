---
doc_id: DEMO-ARCH-BUNDLE-001
title: Demo Merged Architecture Docs
doc_type: architecture_bundle
status: accepted
owner_role: principal_architect
accountable_role: head_of_engineering
source_of_truth: false
version: '1.0'
---

# Demo Merged Architecture Docs

This folder is a flattened architecture bundle for demo execution.

## Purpose
- Present a single architecture source for MCP `docs-graph` during demos.
- Avoid cross-root lookup complexity while preserving coverage from both source sets.

## Included Sources
- `Docs/RefactoredTechnicalDocs/00-architecture`
- `Docs/ConcretePOCProduct/02-architecture`

## Traceability
- File-level source mapping is tracked in `SOURCE-MANIFEST.yaml`.
- Canonical edits should still be made in the original source roots, then re-merged.
