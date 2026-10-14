# ADR — architecture rules

In this repository, ADR means the team's **architecture rules**: testable, technology-neutral statements describing what the architecture and its components shall guarantee. The team has not yet specified a longer expansion of the initials. These files are **not Architecture Decision Records**. Rationale for selected designs and technologies belongs in [`../design-decisions/`](../design-decisions/README.md).

Derive each rule from one or more [software requirements](../requirements/README.md). Use a stable ID such as `AR-DATA-001`. Write one obligation per **shall** statement, identify the responsible component or boundary, and specify how it will be verified. Do not name a database, framework, model, or cloud product in a rule unless that product is itself an approved constraint.

## Rule groups

| File | Architecture concern | Status |
| --- | --- | --- |
| [System boundaries](system-boundaries.md) | Ownership, separation, trust boundaries | Open |
| [Knowledge lifecycle](knowledge-lifecycle.md) | Ingestion, provenance, updates, deletion | Open |
| [Identity and access](identity-and-access.md) | Authentication, authorization, enforcement | Open |
| [Data and persistence](data-and-persistence.md) | Stored information, integrity, queries, recovery | Open |
| [Retrieval and answers](retrieval-and-answers.md) | Grounding, citations, uncertainty | Open |
| [Onboarding](onboarding.md) | Paths, tutoring, progress, assessment if included | Open |
| [Interfaces and MCP](interfaces-and-mcp.md) | Contracts and consistent behavior | Open |
| [Operations](operations.md) | Observability, failure, cost, maintenance | Open |

## Rule format

| ID | Shall statement | Source requirement(s) | Applies to | Verification method | Status |
| --- | --- | --- | --- | --- | --- |

Statuses: Proposed, Accepted, Deferred, Superseded. A proposed statement is not an approved rule.
