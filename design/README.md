# System design

Describe **how** the accepted [software requirements](../requirements/README.md) and [architecture rules](../adr/README.md) will be satisfied. Name chosen technologies only after requirements and rules are clear. Every significant choice should have a rationale in [`../design-decisions/`](../design-decisions/README.md).

| File | Design concern | Status |
| --- | --- | --- |
| [System context](01-system-context.md) | Actors, external systems, boundaries | Open |
| [Component architecture](02-component-architecture.md) | Components and responsibilities | Open |
| [Knowledge pipeline](03-knowledge-pipeline.md) | Ingestion, update, provenance | Open |
| [Domain and data model](04-domain-and-data-model.md) | Entities, relationships, ownership | Open |
| [Database design](05-database-design.md) | Storage, schema, indexes, migrations | Open |
| [Identity and access design](06-identity-and-access.md) | Policy enforcement and data flow | Open |
| [Retrieval and answer design](07-retrieval-and-answering.md) | Search, grounding, citations | Open |
| [Onboarding design](08-onboarding.md) | Paths, tutoring, progress if included | Open |
| [UI design](09-user-interface.md) | Screens, states, accessibility | Open |
| [API and MCP design](10-api-and-mcp.md) | Contracts, tools, errors | Open |
| [Deployment and operations](11-deployment-and-operations.md) | Runtime, security, observability | Open |
| [Failure and recovery](12-failure-and-recovery.md) | Degraded behavior and restoration | Open |
| [Technology selection](13-technology-selection.md) | Candidate comparison and selected stack | Open |
| [System map](14-system-map.md) | Integrated view of the accepted design | Open |
| [Threat model](15-threat-model.md) | Assets, boundaries, misuse, mitigations | Open |

## Design review rule

For each design element, record the requirement or rule it serves, the chosen approach, important alternatives, verification evidence, and open risks. Do not turn an untested assumption into an accepted design.
