# ForceMax Capability Knowledge Base

This folder contains the governed industry taxonomy and L1–L3 capability catalogue for ForceMax Enterprise One.

## Baseline
- 61 industries: IND-001–IND-061 (the authoritative user-supplied taxonomy).
- 15 universal L1 capability domains.
- Industry capability hierarchy: L1 → L2 → L3.
- Healthcare - Private Sector and Healthcare - Public Sector are separate.
- Wholesale is not included; it was an extra 62nd entry in the later Explorer, not in the authoritative 61-industry baseline.

## Files
- [Industry Capability Knowledge Base JSON](industry-capability-knowledge-base.v1.0.0.json) — canonical structured dataset.
- [Industry Taxonomy CSV](industry-taxonomy.v1.0.0.csv) — one row per industry.
- [Capability Catalog CSV](capability-catalog.v1.0.0.csv) — normalized capability rows for analytics and loading.
- [Ontology specification](../docs/metamodel/industry-capability-ontology.md).
- [Knowledge base JSON Schema](../docs/metamodel/schemas/industry-capability-knowledge-base.schema.json).

## Governance status
The imported Explorer structures are proposed candidates. Generic repeated L2/L3 branch patterns are explicitly flagged and require substantive industry-specific refinement and SME approval before production use.
