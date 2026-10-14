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
| SR-SEC-002 | For ordinary team onboarding in the employee interface, return team-specific knowledge only for the employee's invited team, plus company-wide shared knowledge. | SOW milestones 1 and 4 | No other team's team-specific content returned in ordinary team onboarding | Prototype | Repeat onboarding requests using employees invited to two different teams. | Draft |
| SR-SEC-003 | Allow only team admins and the Django superuser to assign an individual learning topic to an employee. | UC-03; SOW milestone 7 | Team admin or superuser role required | Prototype | Try assignment as a team admin, superuser, and employee. | Draft |
| SR-SEC-004 | In the first company-chatbot integration, make all scraped documents available through the MCP to signed-in employees and admins regardless of their team. | UC-05; SOW milestone 6 | All scraped documents accessible to signed-in employees and admins | First chatbot iteration | Request documents from two teams using the chatbot. | Draft |
| SR-SEC-006 | Prevent an employee from changing their team association without accepting an invitation initiated by the destination team's admin or the superuser. | UC-09 | No self-service team transfer | Prototype; phase open | Try direct team change, then complete an authorized invited transfer. | Draft |
| SR-SEC-007 | Associate an invitation recipient's new account with the team named in the accepted invitation. | UC-08; SOW milestone 1 | Invitation determines initial team | Prototype | Accept an invitation and inspect the new account's team. | Draft |
| SR-SEC-008 | Allow an admin to invite people only to teams that admin administers. | UC-07; SOW milestone 1 | No invitations to other admins' teams | Prototype | Attempt invitations to the admin's team and another team's roster. | Draft |
| SR-SEC-009 | Allow the Django superuser to invite people to any team. | UC-07; SOW milestone 1 | No team restriction for the superuser's invitations | Prototype | As superuser, send invitations to two different teams. | Draft |
| SR-SEC-010 | Allow only the Django superuser to appoint a team admin. | UC-10; SOW milestone 1 | Team-admin appointments require superuser authority | Prototype | Appoint a team admin as superuser; reject the same action from a team admin account. | Draft |
| SR-SEC-011 | In the employee interface, allow the assigned employee to access another team's documents used for an explicitly assigned learning path, without expanding access to those documents through ordinary team onboarding or for other employees. | UC-04; SOW milestone 7 | Access limited to the assigned employee and path | Prototype | Assign a cross-team topic, verify the assigned employee can open its path and source content, then verify ordinary onboarding and another employee's path do not gain that content. | Draft |
| SR-SEC-012 | Allow a team admin to assign an individual learning topic only to employees on a team that admin administers. | UC-03; SOW milestone 7 | No cross-team employee assignments by a team admin | Prototype | Assign to an employee on the admin's team and reject an assignment to an employee on another team. | Draft |
| SR-SEC-013 | Allow the Django superuser to assign an individual learning topic to an employee on any team. | UC-03; SOW milestone 7 | No team restriction for superuser assignments | Prototype | As superuser, assign topics to employees on two different teams. | Draft |

**First chatbot iteration:** The chatbot and employee interface have different document access policies. The chatbot exposes all scraped documents to signed-in employees and admins. Ordinary team onboarding in the employee interface uses the employee's team documents and company-wide shared documents; an explicit individual assignment can grant that employee access to another team's documents for the assigned path. The team intends to consider configurable all-document or team-only chatbot access in a later iteration.

## Access examples for later tests

| Actor / role | Information or action | Expected allow / deny behavior | Related requirement |
| --- | --- | --- | --- |
| Signed-out person | Employee or admin interface, company chatbot MCP access, and admin actions | Deny | SR-SEC-001 |
| Employee invited to team A | Team A and company-wide shared knowledge in employee interface | Allow | SR-SEC-002, SR-SEC-007 |
| Employee invited to team A | Team B team-specific knowledge in ordinary team onboarding | Deny | SR-SEC-002 |
| Employee invited to team A with an explicit cross-team topic assignment | Team B documents used for that assigned path | Allow for the assigned path | SR-SEC-011 |
| Another employee without that assignment | Team B documents through the assigned path | Deny | SR-SEC-011 |
| Signed-in employee or admin using company chatbot | Scraped documents from any team through the chatbot | Allow in first iteration | SR-SEC-001, SR-SEC-004 |
| Employee | Assign an individual learning topic | Deny | SR-SEC-003 |
| Admin of team A | Assign an individual learning topic to an employee of team A | Allow | SR-SEC-003, SR-SEC-012 |
| Admin of team A | Assign an individual learning topic to an employee of team B | Deny | SR-SEC-012 |
| Django superuser | Assign an individual learning topic to an employee of team A or team B | Allow | SR-SEC-013 |
| Admin of team A | Invite a person to team B | Deny | SR-SEC-008 |
| Django superuser | Invite people to team A or team B | Allow | SR-SEC-009 |
| Django superuser | Appoint a team admin | Allow | SR-SEC-010 |
| Team admin | Appoint another team admin | Deny | SR-SEC-010 |
| Employee | Change to another team without a new invitation | Deny after the initial team association | SR-SEC-006 |
