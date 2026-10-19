# ADR — architecture rules

In this repository, **ADR means the team's architecture rules**: testable, preferably technology-neutral **shall** statements for components and their interactions. It is not a folder for Architecture Decision Records. Requirements say what the system must do; these rules say what the architecture must guarantee to make that possible; [`../design/`](../design/README.md) says how it will do so.

| File | Rule area |
| --- | --- |
| [System boundaries](01-system-boundaries.md) | Responsibilities, external dependencies, trust boundaries |
| [Data and knowledge](02-data-and-knowledge.md) | Data-layer guarantees, source lifecycle, provenance |
| [Identity and access](03-identity-and-access.md) | Policy and enforcement across paths |
| [Answers and onboarding](04-answers-and-onboarding.md) | Grounding, citations, learning behavior if included |
| [Interfaces and operations](05-interfaces-and-operations.md) | Contracts, failures, observability, recovery |

## Rule format

| ID | The architecture shall... | Source requirement ID | Applies to | How verified | Status |
| --- | --- | --- | --- | --- | --- |

Use a stable ID such as `AR-DATA-001`; link each rule to an accepted software requirement or approved constraint. Keep technology choices and rationale in the relevant design file. If a product is an explicit approved constraint, say so; otherwise avoid naming it in the rule.

## Current review state

The rule tables began as a derivation from the team's completed requirements questionnaire. Review each rule against its linked requirement before accepting it or using it to settle a component or technology choice. The team has accepted AR-SYS-001 through AR-SYS-004; other rules remain drafts until reviewed. The team has also resolved the post-completion deletion question: retain a completion record and source association, while deleting generated path content and steps. See [data and knowledge](02-data-and-knowledge.md).
