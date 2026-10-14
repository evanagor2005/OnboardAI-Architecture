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
| SR-FUNC-009 | Let an employee select one team at the start of the early prototype without an admin assigning that team, and immediately use that selection as the employee's team association. | UC-06; SOW milestone 1 | Early prototype | Sign in as an employee, select a team, and confirm that team's knowledge is used for onboarding. | Draft |
| SR-FUNC-010 | Associate each employee with exactly one team for onboarding in the prototype. | UC-06; SOW milestones 1 and 4 | Prototype | Check the employee's team association and team-based path. | Draft |
| SR-FUNC-011 | Determine the employee's team from role information associated with their authenticated identity when identity integration is introduced during UI/UX improvement. | UC-06; SOW milestone 6 | Later prototype phase | Sign in with accounts mapped to different teams and confirm the correct team is applied without employee selection. | Draft — identity provider undecided |
| SR-FUNC-012 | Present each generated learning path as ordered learning steps with a summary and source link for each step. | UC-02, UC-04; SOW milestones 2 and 7 | Prototype | Generate team and individual-topic paths and inspect their ordering, summaries, and links. | Draft |
| SR-FUNC-013 | Let an admin initiate an email invitation for a person to join a specified team. | UC-07 | Prototype; phase open | Initiate an invitation and inspect its destination team and delivery result. | Draft — inviting admin scope open |
| SR-FUNC-014 | When an invitation recipient accepts and chooses a username and password, create an account associated with the invited team. | UC-08 | Prototype; phase open | Accept an invitation and verify the new account and team association. | Draft |
| SR-FUNC-015 | Change an employee's team only through an invitation initiated by an admin of the destination team and accepted by the employee. | UC-09 | Prototype; phase open | Attempt a self-service team change, then complete a destination-team invitation and acceptance. | Draft |
| SR-FUNC-016 | Provide a Django superuser as the highest level of administration. | Team direction | Prototype; phase open | Sign in as superuser and verify its administrative role. | Draft — detailed powers open |
