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

The team's requirements questionnaire is complete for this round. The shall statements remain drafts until team review and approval. The following choices are deliberately deferred to design or source selection:

**Path-model revision needed:** The team has since chosen team-owned paths with per-employee progress. A path is assigned to all or designated team members; every visible path is assigned for completion, with no required/optional setting. Path assignment does not narrow document access. An admin reviews a new generated path before publication; later source-driven changes publish automatically after successful regeneration. This differs from the older employee-requested generation and post-completion path-deletion wording in the statement of work and requirements. See the [data model design](../design/02-data-and-database.md). Revise affected use cases, shall statements, and milestones; do not treat the older wording as a final decision.

**Project-model revision needed:** The team now distinguishes non-team-owned Projects from team paths. Projects form a shared catalog: a team admin may assign a Project created by another team's admin to an employee on a team they administer. Projects and employees have a many-to-many relationship: one reusable Project may be assigned to multiple employees, and one employee may have multiple Projects, each with separate progress. The individual-topic learning requirements need to adopt this terminology and relationship after the remaining Project assignment details are settled. See the [data model design](../design/02-data-and-database.md).

- The team decided to retain a record identifying the employee and completed path. Its newer team-owned path decision means shared path content remains available after one employee finishes; the older instruction to delete the generated path and steps needs revision. What employee-specific progress is kept or deleted, and how to identify affected employees for later source-change cautions, remain open. No per-step history or completion-to-source association has been approved for completed employees.
- Access and refresh behavior for the website or wiki will be set when the exact second source is selected.
- Invitation expiration duration, the test criterion for an obvious AI-inferred step, and evaluation thresholds belong in design.
- The company chatbot's own data retention and MCP registration capabilities must be checked when that chatbot is selected. OnboardAI itself shall not retain chatbot questions or answers.
