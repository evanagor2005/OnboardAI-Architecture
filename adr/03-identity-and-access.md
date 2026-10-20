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
| AR-ACCESS-002 | Apply team membership and each team path's all-member or selected-member audience to employee path visibility; do not use the owning team to claim exclusive ownership of supporting documents. | SR-FUNC-022, SR-FUNC-029, SR-SEC-002 | Employee path listing and authorization | Compare all-member and selected-member path visibility for teammates and an employee of another team. | Draft — reconciled |
| AR-ACCESS-003 | Apply explicit Project assignments to employee Project visibility and source-link access without exposing the Project in another employee's path list. | SR-DATA-008, SR-SEC-011 | Project assignment and employee path listing | Open a shared Project and all its linked sources as two assignees; verify an unassigned employee does not see the Project. | Draft — reconciled |
| AR-ACCESS-004 | Apply the first company-chatbot policy separately from the employee-interface policy: signed-in employees and admins may retrieve all scraped documents through MCP regardless of team. | SR-FUNC-008, SR-DATA-007, SR-SEC-004 | MCP authorization and retrieval | Request two teams' documents through MCP as signed-in users and deny a signed-out request. | Draft — derived |
| AR-ACCESS-005 | Restrict a team admin to inviting people into administered teams and assigning Projects to employees of administered teams. Only the Django superuser may create teams; the superuser may invite or assign across teams and appoint their admins. An appointed team admin may appoint another admin only for a team they administer. | SR-FUNC-002, SR-FUNC-013, SR-FUNC-017, SR-FUNC-018, SR-SEC-008, SR-SEC-009, SR-SEC-010, SR-SEC-012, SR-SEC-013 | Admin authorization | Test superuser-only team creation and allowed and denied invitations, Project assignments, and appointments across two teams. | Accepted — team decision |
| AR-ACCESS-006 | Bind each account's single onboarding team to an accepted invitation; change that association only after acceptance of an authorized destination-team invitation. | SR-FUNC-010, SR-FUNC-014, SR-FUNC-015, SR-SEC-006, SR-SEC-007 | Invitation and team membership | Inspect account creation and transfer; reject a direct team change. | Draft — derived |
| AR-ACCESS-007 | Enforce one-use and expiration checks when accepting an invitation. | SR-FUNC-014, SR-SEC-014 | Invitation acceptance | Accept once; reject reuse and expiration. | Draft — derived |
| AR-ACCESS-008 | Check the user's appointment for the target team before allowing admin-interface review of its path and linked sources; do not use that appointment to assign the path in the employee interface. | SR-SEC-016 | Admin path and source review; employee path listing | Review an HR path and linked source as an appointed HR admin whose employee team is Software; verify HR paths remain absent from employee "My Paths". | Draft — derived |
| AR-ACCESS-009 | Allow a signed-in team admin to inspect documents in the common indexed pool while creating or reviewing a Project; require an explicit Project assignment for an employee to see that Project in the employee interface. | SR-FUNC-033, SR-SEC-011; team decision | Admin Project creation and review; employee Project listing | Generate and review a Project using documents also used by another team's path; verify assignees see the Project and an unassigned employee does not. | Accepted — reconciled with common-pool decision |
| AR-ACCESS-010 | Make every original-source link included in an employee's assigned team path or Project openable by that employee, regardless of which team path also uses the document. | SR-INT-013; team decision | Path publication, source references, employee interface | As the intended employee, open each original-source link in an assigned path; verify that a document reused by paths for different teams is not made exclusive to either path's team. | Accepted — team decision |
