# ForceMax Enterprise One — Capability and Industry Ontology

**Version:** 1.0.0-draft  
**Namespace:** `fm.capability`  
**Status:** Draft reference ontology; industry models require SME validation  
**Baseline:** 61 authoritative industry categories (IND-001–IND-061), 15 universal L1 domains, L1–L3 decomposition

## 1. Purpose

Define the semantic foundation for discovering, classifying, composing, assessing and governing enterprise capabilities across industries. The ontology is the conceptual contract; the knowledge base contains versioned instances and relationships.

A capability is an enduring, outcome-oriented ability to achieve a business result by combining people, processes, information, technology, assets and governance. It is not a workflow, task, department, application, data object, product or factory.

## 2. Ontology layers

1. **Universal capability layer** — cross-industry abilities represented by the 15 universal L1 domains U01–U15.
2. **Industry capability layer** — value-chain, operating-model and regulatory-context capabilities for the 61 industries.
3. **Specialized capability layer** — sub-industry, business-model, product, geography and specialist operating-context extensions.
4. **Enterprise-local layer** — governed capabilities unique to an enterprise or business unit, with lineage and a promotion path.

Layer and decomposition depth are independent. A specialized capability may be L1, L2 or L3.

## 3. Decomposition levels

- **L1:** major capability domain.
- **L2:** coherent branch within an L1.
- **L3:** reusable capability component with a bounded business outcome.
- Deeper levels may be introduced by governance where they add meaningful ownership, composition or assessment value.

L1–L3 are capability hierarchy levels, not process phases or organization layers.

## 4. Core classes

| Class | Meaning | Key attributes |
|---|---|---|
| Industry | Governed industry category | id, canonicalName, description, classificationType, parentIndustryId, aliases, lifecycleState, provenance |
| Capability | Enduring business ability | id, canonicalName, definition, level, layer, parentId, scope, outcomes, lifecycleState, version |
| CapabilityDomain | L1 capability grouping | domainId, name, industryContext |
| SpecializedContext | Sub-industry or business-model overlay | contextType, contextId, jurisdiction, applicability |
| ApplicabilityAssertion | Contextual decision about a capability | state, rationale, evidence, confidence, reviewer |
| CapabilityRelationship | Typed semantic edge | sourceId, targetId, relationshipType, direction, evidence |
| ValueStream | End-to-end value realization path | id, name, stages, outcomes |
| BusinessProcess | Repeatable sequence realizing capabilities | id, name, owner, processReference |
| OrganizationUnit / Role | Accountability and execution context | id, name, responsibility |
| InformationConcept | Business information used or produced | id, name, sensitivity, stewardship |
| Application / Technology | Enabling solution or platform | id, name, technologyType |
| Risk / Control / Obligation | Exposure and assurance context | id, type, jurisdiction, source |
| FactoryBlueprint / FactoryInstance | Repeatable production/evolution mechanism | id, version, realizationScope |
| Evidence / Provenance | Source and validation record | source, author, date, rationale, confidence, reviewer |

## 5. Capability identity and naming

- IDs are immutable and never reused.
- Canonical names are stable; aliases preserve industry vocabulary.
- Rename without semantic change retains identity.
- Material semantic change creates a new version or successor capability.
- Industry IDs in this baseline are IND-001 through IND-061, preserving the user-supplied order.
- Imported industry capability IDs use stable ForceMax identifiers and retain original Explorer IDs in `sourceId`.

## 6. Relationship vocabulary

| Relationship | Semantics |
|---|---|
| `parent-of` / `child-of` | Hierarchical decomposition |
| `specializes` | Child preserves parent semantics and adds context |
| `extends` | Context-specific extension of a reusable capability |
| `reuses` | Same semantic capability; reference, do not duplicate |
| `depends-on` | Capability requires another capability |
| `enables` | Capability materially enables another |
| `overlaps-with` | Potential semantic overlap requiring review |
| `collaborates-with` | Capabilities jointly contribute to an outcome |
| `realized-by` | Capability is realized by process, organization, application or factory |
| `governed-by` | Capability is constrained by control, policy or obligation |
| `measured-by` | Capability outcome is evaluated by a metric |
| `equivalent-to` | Reviewed semantic equivalence across taxonomies |
| `supersedes` | Versioned successor relationship |
| `mapped-to` | Crosswalk to an external classification or reference model |

## 7. Applicability states

Applicability must be explicit; missing mappings are never interpreted as universal applicability.

- `universal` — underlying ability is relevant across enterprise contexts.
- `contextualized` — relevant with industry-specific definition or constraints.
- `conditional` — applies only when a stated business or regulatory condition holds.
- `not-applicable` — reviewed and explicitly excluded.
- `unassessed` — no validated decision exists.

## 8. Extension semantics

- **Reuse:** reference the universal definition where meaning is identical.
- **Specialization:** retain parent semantics and add industry-specific scope/outcomes.
- **Addition:** create a genuinely new industry ability and state dependencies.
- **Alias:** preserve alternate wording without creating a duplicate capability.
- **Replacement proposal:** require approval, migration and lineage; never silently overwrite a canonical capability.

## 9. Knowledge graph model

The knowledge base is a property graph serialized as JSON:
- Nodes: Industry, Capability, SpecializedContext, ValueStream, Process, OrganizationRole, InformationConcept, Application, Technology, Risk, Control, Obligation, Metric, FactoryBlueprint, Evidence and ExternalReference.
- Edges: typed relationships from Section 6 plus `applies-to`, `classified-as`, `supported-by`, `produces`, `consumes` and `owned-by`.
- Every edge has a stable ID, provenance and lifecycle state.
- Capability hierarchy is represented both as nested structure for convenient traversal and as explicit parent-child graph edges in graph exports.

## 10. Governance and quality gates

Every publishable capability requires stable ID, canonical name, outcome-oriented definition, level, layer, parent, scope, outcomes, lifecycle, version and provenance. Industry extensions additionally require industry context, extension type and universal lineage where applicable.

Validation must detect:
- Duplicate IDs and canonical-name collisions.
- Orphan parents and invalid hierarchy depth.
- Cycles in dependency/specialization relationships.
- Generic template repetition masquerading as industry specificity.
- Unresolved universal/industry semantic overlap.
- Missing definitions, outcomes, scope, owners and evidence.
- Unreviewed applicability assertions and unsupported crosswalks.

## 11. Source reconciliation and known limitation

The user-authoritative taxonomy supplied on 2026-11-23 is **61 industries**, ordered IND-001–IND-061 and ending with Wealth Management. The later uploaded Explorer contains 62 entries and adds Wholesale as entry 62. This knowledge base excludes Wholesale to preserve the authoritative 61-category baseline. Healthcare - Private Sector and Healthcare - Public Sector remain separate.

The uploaded Explorer's L1–L3 structures are imported as proposed source candidates, not certified industry models. The source uses recurring generic branches (strategy/planning; work allocation/scheduling/execution; regulatory/safety/compliance assurance; performance/improvement). These patterns are retained for traceability but flagged for remediation. They must be replaced or substantiated by domain-specific value-chain capabilities through industry SME review.

## 12. Repository artifacts

- `knowledge-base/industry-capability-knowledge-base.v1.0.0.json` — canonical instance catalogue.
- `knowledge-base/industry-taxonomy.v1.0.0.csv` — industry registry.
- `knowledge-base/capability-catalog.v1.0.0.csv` — normalized L1–L3 rows.
- `docs/metamodel/schemas/industry-capability-knowledge-base.schema.json` — machine-readable interchange contract.
