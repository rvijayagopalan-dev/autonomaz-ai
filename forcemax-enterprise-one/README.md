# ForceMax Enterprise One

Product workspace for the ForceMax Enterprise One Autonomous Enterprise Operating Platform. This scaffold separates product documentation, applications, domain services, shared packages, factories, infrastructure, contracts, tests and demonstrations.

## Product baseline
See the [Product Specification and Implementation Blueprint](docs/product/PRODUCT-SPECIFICATION-AND-IMPLEMENTATION-BLUEPRINT-v1.0.md) in the repository documentation.

## Status
This directory structure is an implementation scaffold. Empty capability areas are not yet implemented; see the product roadmap and release acceptance criteria before treating any capability as production-ready.

## Industry capability ontology and knowledge base

The governed baseline contains **61 industries (IND-001–IND-061)**, **15 universal L1 domains**, and industry-specific L1–L3 candidate capability hierarchies.

- [Capability and Industry Ontology](docs/metamodel/industry-capability-ontology.md)
- [Knowledge Base JSON Schema](docs/metamodel/schemas/industry-capability-knowledge-base.schema.json)
- [Knowledge Base guide](knowledge-base/README.md)
- [Canonical industry capability knowledge base](knowledge-base/industry-capability-knowledge-base.v1.0.0.json)
- [Industry taxonomy CSV](knowledge-base/industry-taxonomy.v1.0.0.csv)
- [Normalized L1–L3 capability catalog CSV](knowledge-base/capability-catalog.v1.0.0.csv)

**Governance note:** These are draft reference models. The imported Explorer contains generic repeated L2/L3 operating-pattern branches, which are flagged for industry SME validation and substantive refinement. The authoritative 61-category taxonomy ends with Wealth Management; the extra Wholesale entry in the later 62-entry Explorer is excluded.
