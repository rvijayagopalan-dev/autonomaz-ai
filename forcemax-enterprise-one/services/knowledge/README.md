# Knowledge Service

Knowledge ingestion, source provenance, authorization-aware retrieval, ontology and knowledge graph capabilities.

## ForceMax capability knowledge integration

The service owns ingestion, schema validation, versioned catalogue access, source provenance, authorization-aware retrieval and graph synchronization.

Canonical seed assets:
- `../../knowledge-base/industry-capability-knowledge-base.v1.0.0.json`
- `../../knowledge-base/capability-knowledge-graph.v1.0.0.json`
- `../../knowledge-base/relationship-vocabulary.v1.0.0.md`

Architecture contract: [Capability Intelligence Engine](../../docs/architecture/capability-intelligence-engine-v1.0.0.md).

Initial graph relationships are source-derived only. Applicability and semantic mappings remain unassessed until reviewed. This service must enforce tenant scope, RBAC, provenance, version pinning and audit for all writes.
