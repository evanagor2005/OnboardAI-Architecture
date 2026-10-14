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
| SR-FUNC-006 | Allow a team admin to assign an employee on that admin's team a specific topic contained in the documentation hub. | UC-03; SOW milestone 7 | Prototype | Assign a topic to an employee on the admin's team and confirm it is associated with that employee. | Draft |
| SR-FUNC-007 | Provide the assigned employee a learning path for that specific topic using relevant hub documents. | UC-04; SOW milestone 7 | Prototype | Open the assigned topic as that employee and inspect the path and sources. | Draft |
| SR-FUNC-008 | Provide source-backed knowledge from all scraped documents to signed-in employees and admins using the company chatbot through the MCP in its first iteration, regardless of team association. | UC-05; SOW milestone 6 | First chatbot iteration | Ask through the registered chatbot for documents from two teams and inspect the returned knowledge and sources. | Draft |
| SR-FUNC-010 | Associate each employee with exactly one team for onboarding in the prototype. | UC-08; SOW milestones 1 and 4 | Prototype | Check the invited employee's team association and team-based path. | Draft |
| SR-FUNC-012 | Present each generated learning path as ordered learning steps with a summary for each step and a source link for each source-backed step. | UC-02, UC-04; SOW milestones 2 and 7 | Prototype | Generate paths and inspect their ordering, summaries, and source-backed links. | Draft |
| SR-FUNC-013 | Let the Django superuser invite a person by email to any team, and let a team admin invite a person by email only to a team they administer. | UC-07; SOW milestone 1 | Prototype | Invite a person as superuser to two different teams; invite as team admin to that admin's team and reject an attempt to invite to another team. | Draft |
| SR-FUNC-014 | When an invitation recipient accepts and chooses a username and password, create an account associated with the invited team. | UC-08; SOW milestone 1 | Prototype | Accept an invitation and verify the new account and team association. | Draft |
| SR-FUNC-015 | Change an employee's team only through an invitation initiated by the destination team's admin or the superuser and accepted by the employee. | UC-09 | Prototype; phase open | Attempt a self-service team change, then complete an authorized destination-team invitation and acceptance. | Draft |
| SR-FUNC-016 | Provide a Django superuser as the highest level of administration, including permission to appoint team admins and invite a person to any team. | Team direction; SOW milestone 1 | Prototype | Sign in as superuser, appoint a team admin, and invite people to two different teams. | Draft — other powers open |
| SR-FUNC-017 | Let the Django superuser appoint an admin for a team. | UC-10; SOW milestone 1 | Prototype | Appoint an admin and verify that account gains admin authority for the specified team. | Draft |
| SR-FUNC-018 | Allow the Django superuser to assign an employee on any team a specific topic contained in the documentation hub. | UC-03; SOW milestone 7 | Prototype | As superuser, assign topics to employees on two different teams and verify each assignment reaches the intended employee. | Draft |
| SR-FUNC-019 | When documentation omits a step that has no other logical way to be completed, allow the AI to include that step in a generated path and visibly identify it as an AI inference rather than a documented fact. | UC-02; SOW milestone 2 | Prototype | Use a test corpus with a deliberately omitted obvious step and inspect its label and lack of fabricated source attribution. | Draft — criterion for an obvious step open |
| SR-FUNC-020 | When source documents conflict, present both accounts without favoring either and show each source's available creation or last-updated timestamp. | UC-02, UC-05; SOW milestones 2 and 6 | Prototype | Ingest conflicting test documents with dates and inspect the generated path and chatbot result. | Draft — missing timestamp behavior open |
