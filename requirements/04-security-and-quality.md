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
| SR-SEC-002 | Return only knowledge the requesting employee or admin is permitted to access through both the employee interface and MCP. | SOW milestones 1, 4, and 6 | No restricted cross-team content returned | Prototype | Repeat team-restricted requests through the interface and chatbot. | Draft |
| SR-SEC-003 | Allow only admins to assign an individual learning topic to an employee. | UC-03; SOW milestone 7 | Admin role required | Prototype | Try assignment as an admin and as an employee. | Draft |
| SR-SEC-004 | Apply the requesting person's access rules to company chatbot results. | UC-05; SOW milestone 6 | Same allowed content as the employee interface | Prototype | Compare chatbot and employee-interface results for representative accounts. | Draft |

## Access examples for later tests

| Actor / role | Information or action | Expected allow / deny behavior | Related requirement |
| --- | --- | --- | --- |
| Signed-out person | OnboardAI knowledge and actions | Deny | SR-SEC-001 |
| Employee on team A | Team B restricted knowledge | Deny in employee interface and chatbot | SR-SEC-002, SR-SEC-004 |
| Employee | Assign an individual learning topic | Deny | SR-SEC-003 |
| Admin | Assign an individual learning topic | Allow | SR-SEC-003 |
