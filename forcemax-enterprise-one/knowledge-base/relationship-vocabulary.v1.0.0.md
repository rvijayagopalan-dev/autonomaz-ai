# ForceMax Capability Relationship Vocabulary

**Version:** 1.0.0-draft · **Namespace:** `fm.relationship`

| Relationship | Direction | Meaning | Validation |
|---|---|---|---|
| `parent-of` | Parent → child | Hierarchical decomposition | Acyclic; child level = parent level + 1 |
| `applies-to` | Industry → capability | Capability is in an industry's candidate model | Applicability state required; currently unassessed |
| `specializes` | Specialized → base | Adds context while preserving base semantics | Evidence and semantic-difference statement required |
| `extends` | Extension → base | Adds constraints/outcomes to a reusable capability | Extension type and lineage required |
| `reuses` | Consumer → canonical | Same meaning; points to shared definition | Exact semantic match and reviewer approval |
| `depends-on` | Capability → prerequisite | Required dependency | Dependency rationale; cycle review |
| `enables` | Enabler → outcome capability | Material enabling relationship | Evidence and scope |
| `overlaps-with` | Capability ↔ capability | Potential duplicate or boundary overlap | Review status and resolution |
| `collaborates-with` | Capability ↔ capability | Joint contribution to an outcome | Shared outcome and interaction rationale |
| `realized-by` | Capability → realization | Process, role, application, service or factory realization | Typed target node and coverage scope |
| `governed-by` | Capability → policy/control | Control, policy, regulation or obligation constraint | Jurisdiction and source reference |
| `measured-by` | Capability → metric | Outcome or performance measure | Metric definition, unit and owner |
| `owned-by` | Capability → role/org | Accountability assignment | Principal reference and effective dates |
| `supported-by` | Capability → evidence/system | Evidence or enabling asset | Provenance and lifecycle |
| `mapped-to` | Capability → external reference | Crosswalk to an external framework | Framework/version, mapping type and confidence |
| `supersedes` | Successor → predecessor | Governed semantic successor | Migration mapping and approval |
| `equivalent-to` | Capability ↔ capability | Reviewed semantic equivalence | Bidirectional equivalence evidence |

## Edge envelope

Every edge has: `id`, `sourceId`, `targetId`, `relationshipType`, `lifecycleState`, `provenance`. Context-sensitive edges may also carry `applicabilityState`, `confidence`, `rationale`, `evidenceRefs`, `validFrom`, `validTo`, `reviewer`.

## Graph integrity rules

1. All endpoints must resolve to existing node IDs.
2. IDs are immutable and unique within the catalogue namespace.
3. Parent-child edges must be acyclic and advance exactly one level.
4. A capability can have at most one canonical hierarchy parent within a given model version.
5. Industry applicability is not inferred from a missing edge.
6. `specializes`, `extends`, `reuses`, `equivalent-to` and `depends-on` require rationale and evidence before acceptance.
7. Cross-layer links never duplicate the target capability definition.
8. Deprecated and superseded nodes remain addressable for historical compositions.
