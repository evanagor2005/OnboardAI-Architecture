# Functional requirements

## Questions

- Which use cases from [users and use cases](01-users-and-use-cases.md) are in the prototype?
- What shall each actor be able to start, complete, resume, inspect, or correct?
- What shall the system return on success, insufficient information, denied access, and technical failure?
- Which actions shall knowledge owners or administrators perform, if included?
- Which onboarding, tutoring, assessment, progress, or MCP capabilities are actually in scope?

## Shall statements

| ID | The system shall... | Use case / SOW item | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| SR-FUNC-001 | Authenticate an employee or admin before providing their OnboardAI experience. | SOW milestone 1 | Prototype | Sign in with representative employee and admin accounts. | Draft |
| SR-FUNC-002 | Allow an admin to create a team. | UC-01; SOW milestone 1 | Prototype | Create a team and confirm it is available for onboarding. | Draft |
| SR-FUNC-003 | Show a signed-in software employee basic onboarding information for the software team. | SOW milestone 1 | Prototype | Sign in as a software employee and inspect the displayed information. | Draft |
| SR-FUNC-004 | Create and display a software engineer onboarding path when an employee associated with that team requests one. | UC-02; SOW milestone 2 | Prototype | Request a path and verify it was created from connected knowledge. | Draft |
| SR-FUNC-005 | Create different onboarding paths for employees associated with different teams using knowledge relevant to each team. | UC-02; SOW milestone 4 | Prototype | Request paths as employees from two teams and compare their contents. | Draft |
| SR-FUNC-006 | Allow an admin to assign one employee a specific topic contained in the documentation hub. | UC-03; SOW milestone 7 | Prototype | Assign a topic as an admin and confirm it is associated with the intended employee. | Draft |
| SR-FUNC-007 | Provide the assigned employee a learning path for that specific topic using relevant hub documents. | UC-04; SOW milestone 7 | Prototype | Open the assigned topic as that employee and inspect the path and sources. | Draft |
| SR-FUNC-008 | Provide permitted, source-backed knowledge to the company chatbot through the MCP when a signed-in employee or admin asks a question. | UC-05; SOW milestone 6 | Prototype | Ask through the registered chatbot as an employee and as an admin; inspect the returned knowledge and sources. | Draft |
