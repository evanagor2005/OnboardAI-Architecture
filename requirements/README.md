# Requirements — what the system shall do

Start with the [statement of work](../statement-of-work.md), then define observable behavior and measurable constraints. Do not select databases, frameworks, models, or hosting here.

| File | Decide |
| --- | --- |
| [Users and use cases](01-users-and-use-cases.md) | Who interacts with the system and what tasks they need to complete |
| [Functional](02-functional.md) | Capabilities and success/failure behavior |
| [Knowledge and data](03-knowledge-and-data.md) | Source, provenance, update, deletion, and retention behavior |
| [Security and quality](04-security-and-quality.md) | Access, privacy, accuracy, responsiveness, reliability, accessibility, and constraints |
| [Interfaces](05-interfaces.md) | Behavior visible to people, sources, and approved assistants |
| [Acceptance and verification](06-acceptance-and-verification.md) | What evidence will demonstrate that requirements are met |

## Requirement format

| ID | The system shall... | Source use case / SOW item | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- |

Give each accepted requirement one clear obligation and a stable ID, such as `SR-FUNC-001`. Write `Open` when the team has not decided. Architecture rules in [`../adr/`](../adr/README.md) must cite the requirements they serve.

## Review status

The team's requirements questionnaire is complete for this round. Most shall statements remain drafts until team review and approval; some rows identify a directly confirmed decision. The following choices are deliberately deferred to design or source selection:

**Team-path model:** A team owns many reusable paths. An admin generates a path from a keyword and common-pool evidence, reviews it before first publication, and makes it available to all or selected team members. Every visible path is assigned for completion; there is no separate required/optional setting. Each employee has independent progress. Later successful source-driven revisions publish without another admin review. A document used by a team's path does not become exclusive to that team. See the [data model design](../design/02-data-and-database.md).

**Project model:** Projects are reusable paths without an owning team. They form a shared admin catalog: a team admin may assign a Project created by another admin to an employee on a team they administer. Projects and employees have a many-to-many relationship, with independent progress per employee and Project. The Django superuser may assign Projects across teams. See the [data model design](../design/02-data-and-database.md).

**Project generation:** An admin supplies a keyword to generate a reusable Project from the common indexed pool. Generation searches the full common pool. There is no Project team filter, and source documents are not owned by the team that uses them. Each assigning admin reviews the Project before that admin's assignment becomes visible to its employee, including when another admin previously assigned the same Project. Successful source-driven revisions become visible automatically to existing assignees without another review. The prototype assumes indexed documents are not confidential and lets team admins inspect sources during Project review.

**Source pool and employee access:** Documents form a common pool for admin-created paths; the same document may support paths for different teams. The employee interface lists paths based on team membership, path audience, and Project assignments. An assigned employee can open every original-source link in their path or Project. A separate employee-facing search or browse interface for the whole pool has not been chosen.

- Shared team-path and Project content and steps remain after one employee completes them. Delete that employee's step-progress state and retain a completion record linking the employee to the completed path or Project. If associated source material later changes, a general path-changed warning suffices; no completed-step history is needed. Exact completion fields, source-provenance representation, and retention period remain open.
- Milestone 1 needs only a basic saved team path. Keyword generation and admin review begin with the later dynamic-path milestones in the [statement of work](../statement-of-work.md).
- Assigned employees must be able to open original links from the website or wiki. Its sign-in method and refresh schedule will be set when the exact second source is selected.
- Invitation expiration duration, the test criterion for an obvious AI-inferred step, and evaluation thresholds belong in design.
- The company chatbot's own data retention and MCP registration capabilities must be checked when that chatbot is selected. OnboardAI itself shall not retain chatbot questions or answers.
