# Design — how the system meets its rules

Use accepted [software requirements](../requirements/README.md) and [architecture rules](../adr/README.md) as inputs. Each design file should state the chosen approach, important alternatives, why the team chose it, and how it will be checked. There is **no separate design-decision folder**.

| File | Design area |
| --- | --- |
| [System overview](01-system-overview.md) | Actors, components, boundaries, end-to-end flows |
| [Data and database](02-data-and-database.md) | Domain model, storage, schema, access patterns |
| [Knowledge, retrieval, and AI](03-knowledge-retrieval-and-ai.md) | Source lifecycle, search, grounding, citations |
| [Identity and access](04-identity-and-access.md) | Authentication, policy, enforcement, audit |
| [Onboarding and UI](05-onboarding-and-ui.md) | Paths and learning interactions if included; screens and states |
| [APIs and MCP](06-apis-and-mcp.md) | Internal and external contracts if included |
| [Deployment and operations](07-deployment-and-operations.md) | Runtime, threats, failures, monitoring, recovery |
| [Technology choices](08-technology-choices.md) | Candidate comparison and selected stack |
| [Evaluation plan](09-evaluation-plan.md) | Tests and evidence for requirements and rules |
| [Visuals](visuals/README.md) | Editable diagrams and exports |

## Design entry format

| Requirement / rule IDs | Chosen design | Alternatives considered | Why this choice | Evidence or test | Status |
| --- | --- | --- | --- | --- | --- |

Record unresolved choices as **Open** with an owner and the evidence needed. A design is not accepted merely because a field has been filled in.
