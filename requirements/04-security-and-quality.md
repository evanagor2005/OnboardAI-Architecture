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
| SR-SEC-001 | Require a signed-in identity before an employee or admin accesses OnboardAI knowledge or actions. | SOW milestone 1; UC-02, UC-03, UC-05 | Signed-in users only | Prototype | Attempt access while signed out and while signed in. | Draft |
| SR-SEC-002 | For an employee request, return team-specific knowledge only for that employee's associated team, plus company-wide shared knowledge, through the employee interface and MCP. | SOW milestones 1, 4, and 6 | No content from another team's team-specific documents returned | Prototype | Repeat requests using two employee team associations through the interface and chatbot. | Draft |
| SR-SEC-003 | Allow only admins to assign an individual learning topic to an employee. | UC-03; SOW milestone 7 | Admin role required | Prototype | Try assignment as an admin and as an employee. | Draft |
| SR-SEC-004 | Apply the requesting person's access rules to company chatbot results. | UC-05; SOW milestone 6 | Same allowed content as the employee interface | Prototype | Compare chatbot and employee-interface results for representative accounts. | Draft |
| SR-SEC-005 | Use the employee's selected team as their team association for knowledge filtering in the early prototype. | UC-06; SOW milestone 1 | Selected team and shared content only | Early prototype | Select team A, then check that team A and shared documents are available while team B documents are absent. | Draft |
| SR-SEC-006 | Prevent an employee from changing their team association without accepting an invitation initiated by an admin of the destination team. | UC-09 | No self-service team transfer | Prototype; phase open | Try direct team change, then complete an invited transfer. | Draft — inviting admin scope open |
| SR-SEC-007 | Associate an invitation recipient's new account with the team named in the accepted invitation. | UC-08 | Invitation determines initial team | Prototype; phase open | Accept an invitation and inspect the new account's team. | Draft |

**Early prototype limitation:** Team selection is self-declared. It filters knowledge by the selected team, but does not independently verify the employee's real organizational membership. The later identity integration is intended to provide that association from authenticated role information.

**Open decision:** Which team-specific documents, if any, may an admin access through the company chatbot?

## Access examples for later tests

| Actor / role | Information or action | Expected allow / deny behavior | Related requirement |
| --- | --- | --- | --- |
| Signed-out person | OnboardAI knowledge and actions | Deny | SR-SEC-001 |
| Employee associated with team A | Team A and company-wide shared knowledge | Allow | SR-SEC-002, SR-SEC-005 |
| Employee associated with team A | Team B team-specific knowledge | Deny in employee interface and chatbot | SR-SEC-002, SR-SEC-004 |
| Employee | Assign an individual learning topic | Deny | SR-SEC-003 |
| Admin | Assign an individual learning topic | Allow | SR-SEC-003 |
| Employee | Change to another team without a new invitation | Deny after the initial team association | SR-SEC-006 |
