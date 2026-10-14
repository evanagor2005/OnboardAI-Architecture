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
| SR-SEC-001 | Require a signed-in identity before a person accesses the employee or admin interface or performs admin actions. | SOW milestone 1; UC-02, UC-03 | Signed-in users only for these interfaces | Prototype | Attempt employee and admin actions while signed out and while signed in. | Draft |
| SR-SEC-002 | In the employee interface, return team-specific knowledge only for the employee's invited team, plus company-wide shared knowledge. | SOW milestones 1 and 4 | No other team's team-specific content returned in the employee interface | Prototype | Repeat onboarding requests using employees invited to two different teams. | Draft |
| SR-SEC-003 | Allow only admins to assign an individual learning topic to an employee. | UC-03; SOW milestone 7 | Admin role required | Prototype | Try assignment as an admin and as an employee. | Draft |
| SR-SEC-004 | In the first company-chatbot integration, make all scraped documents available through the MCP to eligible chatbot users regardless of their team. | UC-05; SOW milestone 6 | All scraped documents accessible to eligible chatbot users | First chatbot iteration | Request documents from two teams using the chatbot. | Draft — user eligibility open |
| SR-SEC-006 | Prevent an employee from changing their team association without accepting an invitation initiated by an admin of the destination team. | UC-09 | No self-service team transfer | Prototype; phase open | Try direct team change, then complete an invited transfer. | Draft |
| SR-SEC-007 | Associate an invitation recipient's new account with the team named in the accepted invitation. | UC-08; SOW milestone 1 | Invitation determines initial team | Prototype | Accept an invitation and inspect the new account's team. | Draft |
| SR-SEC-008 | Allow an admin to invite people only to teams that admin administers. | UC-07; SOW milestone 1 | No invitations to other admins' teams | Prototype | Attempt invitations to the admin's team and another team's roster. | Draft |

**First chatbot iteration:** The chatbot and employee interface have different document access policies. The chatbot exposes all scraped documents to eligible chatbot users. Whether those users must be signed in is still open; the team intends to consider configurable all-document or team-only access in a later iteration.

## Access examples for later tests

| Actor / role | Information or action | Expected allow / deny behavior | Related requirement |
| --- | --- | --- | --- |
| Signed-out person | Employee or admin interface and admin actions | Deny | SR-SEC-001 |
| Employee invited to team A | Team A and company-wide shared knowledge in employee interface | Allow | SR-SEC-002, SR-SEC-007 |
| Employee invited to team A | Team B team-specific knowledge in employee interface | Deny | SR-SEC-002 |
| Eligible company chatbot user | Scraped documents from any team through the chatbot | Allow in first iteration | SR-SEC-004 |
| Employee | Assign an individual learning topic | Deny | SR-SEC-003 |
| Admin | Assign an individual learning topic | Allow | SR-SEC-003 |
| Admin of team A | Invite a person to team B | Deny | SR-SEC-008 |
| Employee | Change to another team without a new invitation | Deny after the initial team association | SR-SEC-006 |
