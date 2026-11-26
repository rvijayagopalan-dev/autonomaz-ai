# ForceMax Enterprise One — Capability Intelligence Engine

**Version:** 1.0.0-draft  
**Status:** Architecture and implementation specification  
**Workspace:** `services/knowledge`, `services/architecture`, `services/governance`

## 1. Mission

Turn the 61-industry capability catalogue into a governed intelligence service that can search, traverse, compare, compose, assess and trace enterprise capabilities. The engine must distinguish source facts from inferred suggestions and never publish AI-generated mappings without human approval.

## 2. Logical architecture

```text
Client / Enterprise One UI / Agent Mesh
                 |
          Capability API
                 |
      Capability Intelligence Facade
       |        |          |
   Catalog   Graph      Composition
   Registry  Traversal  & Resolution
       |        |          |
       +---- Knowledge Graph ----+
       |                         |
  Ontology/Schema           Evidence Store
       |                         |
       +---- Governance & Review+
                 |
       Search Index / Analytics / Cache
```

## 3. Core engine capabilities

| Component | Responsibility | Primary operations |
|---|---|---|
| Catalog Registry | Versioned industry and universal catalogue | getIndustry, listIndustries, getCapability, listChildren |
| Graph Store Adapter | Persist and traverse typed nodes/edges | neighbors, ancestors, descendants, path, subgraph |
| Semantic Search | Search names, aliases, definitions and context | searchCapabilities, suggestRelated |
| Relationship Resolver | Detect candidate reuse, overlap, specialization and dependency | proposeRelationship, compareDefinitions |
| Applicability Engine | Evaluate capability applicability by enterprise context | assessApplicability, explainApplicability |
| Composition Engine | Assemble enterprise model from universal + industry + specialization overlays | composeModel, resolveInheritance, detectDuplicates |
| Traceability Engine | Link capabilities to value streams, processes, data, apps, controls, metrics and factories | traceImpact, coverageReport |
| Assessment Engine | Capture maturity, criticality, value and evidence | assessCapability, calculateGap |
| Governance Workflow | Review, approve, version, deprecate and audit changes | submitReview, approve, reject, supersede |
| Quality Engine | Run schema, graph and semantic quality checks | validateCatalogue, detectTemplatePatterns |

## 4. Canonical input and output

Input context:
- Enterprise identity and scope.
- Primary and secondary industry IDs.
- Sub-industry and specialist contexts.
- Business models (B2B, B2C, B2B2C, marketplace, subscription, platform, public service, asset owner/operator).
- Geographies and regulatory jurisdictions.
- Pinned universal and industry catalogue versions.
- Explicit inclusions, exclusions and enterprise-local extensions.

Composition output:
- Resolved capability nodes with original stable IDs.
- Parent/extension/reuse lineage.
- Applicability state and evidence.
- Duplicate and semantic-overlap candidates.
- Dependencies and unresolved conflicts.
- Coverage against selected business scope.
- Reproducible manifest with pinned catalogue and ontology versions.

## 5. Applicability policy

Use only: `universal`, `contextualized`, `conditional`, `not-applicable`, `unassessed`. Unknown means `unassessed`. The initial industry-to-capability graph contains unassessed applicability edges; this is deliberate and avoids asserting that every imported item is valid for every enterprise.

## 6. Composition algorithm

1. Validate requested industry IDs and catalogue versions.
2. Load the pinned universal baseline.
3. Load primary industry and explicitly selected secondary overlays.
4. Apply specialist, business-model, geography and jurisdiction overlays only when selected.
5. Resolve exact reuse by stable canonical ID; do not merge by name alone.
6. Generate candidate duplicate/overlap groups using lexical and semantic similarity.
7. Preserve specialized nodes and their lineage; never overwrite universal definitions.
8. Apply applicability assertions and explicit exclusions.
9. Validate hierarchy, references, conflicts, dependencies and coverage.
10. Emit a versioned composition manifest and human-review queue.

No implicit truncation of secondary industry branches. No automatic acceptance of AI-suggested mappings.

## 7. API contract (logical)

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/v1/industries` | List and filter the 61 industry categories |
| GET | `/v1/industries/{industryId}/capabilities` | Retrieve industry L1–L3 hierarchy |
| GET | `/v1/capabilities/{capabilityId}` | Fetch canonical capability |
| GET | `/v1/capabilities/{capabilityId}/relationships` | Traverse graph relationships |
| POST | `/v1/capabilities/search` | Context-aware capability search |
| POST | `/v1/models/compose` | Compose an enterprise model |
| POST | `/v1/applicability/assessments` | Submit an applicability assertion |
| POST | `/v1/relationships/proposals` | Propose semantic graph relationship |
| POST | `/v1/quality/validate` | Validate a catalogue or composed model |
| POST | `/v1/traceability/impact` | Trace capability impact and dependencies |
| POST | `/v1/governance/reviews` | Submit changes for approval |

All write operations require tenant scope, principal identity, authorization, idempotency key, audit event and provenance. Review and approval are separate permissions.

## 8. Knowledge graph persistence

The canonical interchange format is JSON-LD-compatible node/edge data. A graph database may be selected behind an adapter; the logical model must not depend on one vendor. Retain relational/catalogue storage for versioned records and use graph storage for traversal. Search index is a derived projection, never the system of record.

Initial seed files:
- `knowledge-base/capability-knowledge-graph.v1.0.0.json`
- `knowledge-base/relationship-vocabulary.v1.0.0.md`
- `knowledge-base/industry-capability-knowledge-base.v1.0.0.json`

## 9. Quality and governance gates

- JSON Schema validation and referential integrity.
- Unique IDs, valid parents and no hierarchy cycles.
- Explicit lifecycle, provenance and version.
- Industry-specific semantic coverage; flag repeated generic templates.
- Every accepted semantic edge has rationale, evidence, reviewer and confidence.
- Applicability gaps remain unassessed.
- Composition reproducibility and stable output for pinned inputs.
- Audit log for every proposed/accepted/rejected mutation.
- No AI-only publication or silent semantic merge.

## 10. Implementation sequence

**Sprint 1 — Foundation:** catalog loader, schema validation, graph import/export, deterministic hierarchy traversal, REST read APIs.

**Sprint 2 — Intelligence:** lexical search, faceted filtering, candidate overlap detection, industry comparison, graph visualization.

**Sprint 3 — Composition:** primary/secondary industry overlays, applicability states, deduplication proposals, composition manifest and review queue.

**Sprint 4 — Traceability:** value streams, processes, roles, data, applications, controls, metrics and factory mappings.

**Sprint 5 — Governance:** review workflow, immutable versions, impact analysis, audit events, quality scoring and AI-assisted suggestions.

## 11. Acceptance criteria

1. All 61 industries and 15 universal L1 domains load with stable IDs.
2. L1–L3 traversal returns exact source hierarchy.
3. Every edge endpoint resolves; hierarchy is acyclic.
4. Unknown applicability remains unassessed.
5. Multi-industry composition preserves all selected branches and lineage.
6. Duplicate candidates are explainable and require reviewer disposition.
7. A pinned composition is reproducible.
8. Every accepted mapping is traceable to evidence and an authorized reviewer.
9. Catalogue validation emits actionable errors and quality warnings.
10. APIs enforce tenant isolation, RBAC, audit and version pinning.
