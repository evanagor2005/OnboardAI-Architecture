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

- The team decided to retain a record identifying the employee and completed path, with the source association needed for later change cautions. Generated path content and step details are deleted. The record fields and retention period belong in design.
- Access and refresh behavior for the website or wiki will be set when the exact second source is selected.
- Invitation expiration duration, the test criterion for an obvious AI-inferred step, and evaluation thresholds belong in design.
- The company chatbot's own data retention and MCP registration capabilities must be checked when that chatbot is selected. OnboardAI itself shall not retain chatbot questions or answers.
