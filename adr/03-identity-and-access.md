# Architecture rules — identity and access

## Questions

- What identity and role context shall every protected request carry?
- What shall be checked before content, search results, answers, citations, or MCP outputs are returned?
- How shall all included interfaces receive consistent permission decisions?
- What shall happen when identity or permission data is missing, stale, or unavailable?
- How shall stored, cached, and indexed content preserve access boundaries?
- What access decisions and changes shall be auditable?

## Shall statements

| ID | The architecture shall... | Source requirement ID | Applies to | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| AR-ACCESS-001 | Require an authenticated identity before serving the employee interface, admin interface, or MCP knowledge requests. | SR-FUNC-001, SR-SEC-001 | Authentication and interface entry points | Attempt each action signed out and signed in. | Draft — derived |
| AR-ACCESS-002 | Apply the employee's invited team and shared-document policy to ordinary onboarding retrieval, excluding other teams' specific content. | SR-DATA-005, SR-DATA-006, SR-SEC-002 | Employee interface, retrieval authorization | Compare results for employees invited to two teams. | Draft — derived |
| AR-ACCESS-003 | Apply an explicit individual assignment as a path-scoped grant to its intended employee, including relevant cross-team documents, without expanding ordinary onboarding or another employee's access. | SR-DATA-008, SR-SEC-011 | Assignment, path, source access | Open a cross-team assigned path as the assignee, then test ordinary onboarding and another employee. | Draft — derived |
| AR-ACCESS-004 | Apply the first company-chatbot policy separately from the employee-interface policy: signed-in employees and admins may retrieve all scraped documents through MCP regardless of team. | SR-FUNC-008, SR-DATA-007, SR-SEC-004 | MCP authorization and retrieval | Request two teams' documents through MCP as signed-in users and deny a signed-out request. | Draft — derived |
| AR-ACCESS-005 | Restrict team invitations and individual-topic assignments to the team admin's administered team, while allowing the Django superuser to perform them across teams and appoint team admins. | SR-FUNC-013, SR-FUNC-017, SR-FUNC-018, SR-SEC-008, SR-SEC-009, SR-SEC-010, SR-SEC-012, SR-SEC-013 | Admin authorization | Test allowed and denied invitations, assignments, and appointments across two teams. | Draft — derived |
| AR-ACCESS-006 | Bind each account's single onboarding team to an accepted invitation; change that association only after acceptance of an authorized destination-team invitation. | SR-FUNC-010, SR-FUNC-014, SR-FUNC-015, SR-SEC-006, SR-SEC-007 | Invitation and team membership | Inspect account creation and transfer; reject a direct team change. | Draft — derived |
| AR-ACCESS-007 | Enforce one-use and expiration checks when accepting an invitation. | SR-FUNC-014, SR-SEC-014 | Invitation acceptance | Accept once; reject reuse and expiration. | Draft — derived |
| AR-ACCESS-008 | Check the user's appointment for the target team before allowing admin-interface review of its path and linked sources; do not use that appointment to assign the path in the employee interface. | SR-SEC-016 | Admin path and source review; employee path listing | Review an HR path and linked source as an appointed HR admin whose employee team is Software; verify HR paths remain absent from employee "My Paths". | Draft — derived |
| AR-ACCESS-009 | Allow a signed-in team admin to inspect source documents from any team while creating or reviewing a Project, while keeping ordinary employee onboarding retrieval limited to the employee's team and shared documents and requiring an explicit Project assignment for employee access to cross-team Project sources. | Team decision; Project access requirements revision pending | Admin Project creation and review; employee retrieval | As a Software admin, generate and review a Project using HR sources; verify ordinary Software onboarding excludes HR sources and an assigned employee can open the Project's linked HR sources. | Accepted — team decision |
| AR-ACCESS-010 | Make every original-source link included in an employee's assigned team path or Project openable by that employee, regardless of which team path also uses the document. | SR-INT-013; team decision | Path publication, source references, employee interface | As the intended employee, open each original-source link in an assigned path; verify that a document reused by paths for different teams is not made exclusive to either path's team. | Accepted — team decision |
