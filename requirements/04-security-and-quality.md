# Security and quality requirements

## Questions

- Who shall be allowed to access each kind of information and action?
- What shall happen when identity, permission, or source information is missing?
- What privacy, audit, retention, and deletion behavior is required?
- What accuracy, citation, and uncertainty behavior is required for answers?
- What response time, availability, recovery, accessibility, and usability targets matter?
- What budget, team capacity, data, or course constraints are firm limits rather than preferences?

## Shall statements and measurable constraints

| ID | The system shall... | Scenario / source | Target or limit | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- | --- |
| SR-SEC-001 | Require a signed-in identity before a person accesses the employee or admin interface, uses the company chatbot's MCP connection, or performs admin actions. | SOW milestones 1 and 6; UC-02, UC-03, UC-05 | Signed-in users only for these interfaces | Prototype | Attempt employee, admin, and chatbot actions while signed out and while signed in. | Draft |
| SR-SEC-002 | In the employee interface, show a team path only to members of its owning team who are included in its all-member or selected-member audience; do not infer source-document ownership from path ownership. | SOW milestones 2 and 4 | An unassigned member cannot see a selected-member path or its steps | Prototype | Compare path lists for two teammates and an employee of another team; open linked sources as intended assignees. | Draft — reconciled with common-pool decision |
| SR-SEC-003 | Allow only team admins and the Django superuser to review and assign a Project to an employee; require the assigning admin to review before that employee can see it. | UC-03; SOW milestone 7 | Team admin or superuser role required | Prototype | Try Project assignment as a team admin, superuser, and employee; verify each assignment is hidden until its assigning admin completes review. | Team-confirmed |
| SR-SEC-004 | In the first company-chatbot integration, make all scraped documents available through the MCP to signed-in employees and admins regardless of their team. | UC-05; SOW milestone 6 | All scraped documents accessible to signed-in employees and admins | First chatbot iteration | Request documents from two teams using the chatbot. | Draft |
| SR-SEC-006 | Prevent an employee from changing their team association without accepting an invitation initiated by the destination team's admin or the superuser. | UC-09 | No self-service team transfer | Prototype; phase open | Try direct team change, then complete an authorized invited transfer. | Draft |
| SR-SEC-007 | Associate an invitation recipient's new account with the team named in the accepted invitation. | UC-08; SOW milestone 1 | Invitation determines initial team | Prototype | Accept an invitation and inspect the new account's team. | Draft |
| SR-SEC-008 | Allow an admin to invite people only to teams that admin administers. | UC-07; SOW milestone 1 | No invitations to other admins' teams | Prototype | Attempt invitations to the admin's team and another team's roster. | Draft |
| SR-SEC-009 | Allow the Django superuser to invite people to any team. | UC-07; SOW milestone 1 | No team restriction for the superuser's invitations | Prototype | As superuser, send invitations to two different teams. | Draft |
| SR-SEC-010 | Allow the Django superuser to appoint an admin for any team and an appointed team admin to appoint another admin only for a team they administer. | UC-10; SOW milestone 1 | Team-admin appointments require superuser authority or an appointment for the target team | Prototype | Appoint a team admin as superuser; as an appointed team admin, appoint another admin for the administered team and reject an appointment to another team. | Team-confirmed |
| SR-SEC-011 | Let an assigned employee open every original-source link included in that employee's team path or Project; do not expose an unassigned path or Project through the employee interface. | UC-02, UC-04; SOW milestones 2 and 7 | Source links in assigned paths open; unassigned saved paths remain hidden | Prototype | Use one source in paths for two teams, open it from each assigned path, and verify an unassigned path remains absent. | Draft — reconciled with common-pool decision |
| SR-SEC-012 | Allow a team admin to review and assign a Project only to employees on teams that admin administers. | UC-03; SOW milestone 7 | No assignments outside administered teams | Prototype | Assign to an employee on an administered team and reject an assignment to another team's employee. | Draft — reconciled with team decision |
| SR-SEC-013 | Allow the Django superuser to review and assign a Project to an employee on any team. | UC-03; SOW milestone 7 | No team restriction for superuser assignments | Prototype | As superuser, assign one Project to employees on two different teams. | Draft — reconciled with team decision |
| SR-SEC-014 | Accept each team invitation at most once and only before its expiration. | UC-08; SOW milestone 1 | One use; time limited | Prototype | Accept an invitation, reject a second use, and reject an expired invitation. | Draft — expiration duration in design |
| SR-SEC-015 | Avoid retaining company-chatbot questions and answers in OnboardAI's data store. | UC-05; SOW milestone 6 | No OnboardAI conversation retention | First chatbot iteration | Use the chatbot and inspect OnboardAI's stored data. | Draft |
| SR-SEC-016 | Let an appointed team admin open source documents linked from that team's paths in the admin interface for path review, even when the admin's employee team is different; do not add those paths to the admin's employee path list. | Team path-review decision | Admin access through administered team only; no employee-path assignment from admin role | Prototype | Make a Software employee an HR admin; open an HR path and its linked source in the HR admin interface, then verify HR paths are absent from the employee's "My Paths" list. | Draft — new team direction |

**First chatbot iteration:** The chatbot can retrieve from the entire scraped pool for signed-in employees and admins. The employee interface shows saved team paths according to team membership and each path's audience, plus explicitly assigned Projects. Employees can open original-source links included in those paths. The team has not chosen a separate employee-facing search or browse interface for the whole document pool. Whether later chatbot access should be configurable remains a future consideration.

## Access examples for later tests

| Actor / role | Information or action | Expected allow / deny behavior | Related requirement |
| --- | --- | --- | --- |
| Signed-out person | Employee or admin interface, company chatbot MCP access, and admin actions | Deny | SR-SEC-001 |
| Employee invited to team A | Published all-member team A path and its linked sources | Allow | SR-SEC-002, SR-SEC-011 |
| Team A employee omitted from a selected-member team A path | That path and its steps in the employee interface | Deny | SR-SEC-002 |
| Employee assigned a Project built from the common document pool | Project and its linked original sources | Allow | SR-SEC-011 |
| Another employee without that Project assignment | The Project in the employee interface | Deny | SR-SEC-011 |
| Signed-in employee or admin using company chatbot | Scraped documents from any team through the chatbot | Allow in first iteration | SR-SEC-001, SR-SEC-004 |
| Employee | Assign a Project | Deny | SR-SEC-003 |
| Admin of team A | Review and assign a Project to an employee of team A | Allow | SR-SEC-003, SR-SEC-012 |
| Admin of team A | Assign a Project to an employee of team B | Deny | SR-SEC-012 |
| Django superuser | Review and assign a Project to an employee of team A or team B | Allow | SR-SEC-013 |
| Admin of team A | Invite a person to team B | Deny | SR-SEC-008 |
| Django superuser | Invite people to team A or team B | Allow | SR-SEC-009 |
| Django superuser | Appoint a team admin | Allow | SR-SEC-010 |
| Team admin | Appoint another team admin for an administered team | Allow; deny for other teams | SR-SEC-010 |
| Software employee appointed HR admin | HR path and its linked source documents in HR admin interface | Allow for review; do not add HR path to employee "My Paths" | SR-SEC-016 |
| Employee | Change to another team without a new invitation | Deny after the initial team association | SR-SEC-006 |
