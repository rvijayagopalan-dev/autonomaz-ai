# Capability Knowledge Graph — Seed Validation Report

**Version:** 1.0.0-draft · **Date:** 2026-11-26

## Seed inventory

| Measure | Count |
|---|---:|
| Industry nodes | 61 |
| Universal capability nodes | 295 |
| Industry capability nodes | 5372 |
| Total graph nodes | 5728 |
| Total graph edges | 5652 |
| Industry applicability edges | 316 |
| Hierarchy edges | 5336 |

## Seed semantics

- Industry-to-L1 applicability edges are explicitly **unassessed**.
- Parent-child edges are derived from the nested source hierarchy.
- No semantic equivalence, dependency, specialization or factory-realization links are invented.
- All nodes and edges are proposed and retain source provenance.

## Validation policy

The graph generator creates deterministic IDs and relationship IDs. Downstream CI must validate endpoint existence, unique IDs, parent-child level increments, acyclic hierarchy and count consistency. Semantic relationships require evidence and human review before acceptance.

## Known data quality risks

1. Industry L2/L3 patterns in the source Explorer include repeated generic branches.
2. The source Explorer contained 62 categories; Wholesale was excluded to retain the 61-industry approved working baseline.
3. The source capability models remain unvalidated by industry SMEs.
4. External framework crosswalks and regulatory applicability have not been asserted.
