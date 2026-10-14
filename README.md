# OnboardAI architecture

This repository has one working sequence. Its templates are blank prompts; they do not approve a feature, requirement, rule, or technology.

1. [Statement of work](statement-of-work.md) — what the team commits to deliver and what is out of scope.
2. [Requirements](requirements/README.md) — what the system shall do and how success will be checked.
3. [ADR](adr/README.md) — the team's architecture rules: what components and interactions shall guarantee, derived from requirements.
4. [Design](design/README.md) — how the system will meet those rules, including the data model, selected technologies, and the reasons for major choices.

`ADR` is used here in the team's sense of **architecture rules**, not Architecture Decision Records. Design decisions and their rationale live in the relevant design file; there is no separate decision-record folder. Previous templates remain available in Git history, but are not part of the current workflow.

## How to work through the files

Discuss each question, write the team's answer, and mark it **Accepted**, **Proposed**, **Deferred**, or **Open**. Keep requirements and rules as one testable **shall** statement per row. Link requirement IDs (`SR-...`) to architecture-rule IDs (`AR-...`), then link both to the design and verification evidence. If a capability is outside the prototype, mark it **Not applicable to prototype** rather than filling it as if it were approved.

When a choice needs evidence, record the question, the small test or research needed, and an owner in the relevant file. Do not turn an assumption into an accepted decision.
