# Interface requirements

Describe behavior visible at system boundaries. Leave endpoint names, frameworks, and protocols to design unless already fixed by the statement of work.

## Questions

- Which human-facing interfaces are included?
- Which source systems must provide or receive information?
- Is an MCP interface included; if so, what may approved assistants request and receive?
- What inputs, outputs, citations, denials, and errors shall each interface expose?
- What identity and permission context shall accompany each request?

## Interface inventory

| Interface | External actor or system | Required task | Inputs | Outputs / errors | Scope |
| --- | --- | --- | --- | --- | --- |
| Employee interface | Signed-in employee associated with one invited team | Request and follow a team or individually assigned path | Employee account and team association, path request or explicit assignment | Path with accessible source references, including assigned cross-team content where authorized, or an unavailable/denied result | Prototype |
| Admin interface | Signed-in team admin or Django superuser | Create a team, invite a person to an authorized team, assign an individual topic to an authorized employee, or appoint a team admin as superuser | Admin identity, team and recipient details, employee and topic, or team-admin appointment | Confirmation or failure | Prototype |
| Company chatbot through MCP | Signed-in employee or admin | Retrieve onboarding knowledge from scraped documents | Question and signed-in user identity | Source-backed content from any scraped document, or an unavailable or denied result | First chatbot iteration; registration dependency |
| Documentation ingestion | Connected documentation sources | Supply team knowledge | Source content and team association | Indexed knowledge or ingestion failure | Prototype |
| Team invitation email | Django superuser or admin of destination team, invitation recipient, and Mailgun | Send and accept an invitation to a specific team | Recipient email and destination team | Invitation email or delivery failure; acceptance flow | Prototype; milestone 1 |

## Shall statements

| ID | The system shall... | Interface / use case | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| SR-INT-001 | Let a signed-in employee associated with a team request an onboarding path through the employee interface. | Employee interface; UC-02 | Prototype | Request a path as a software employee and as an employee of another team. | Draft |
| SR-INT-002 | Let a team admin create a team and assign an individual topic to an employee on a team they administer; let the superuser assign a topic to an employee on any team through the admin interface. | Admin interface; UC-01, UC-03 | Prototype | Complete a team-admin assignment to an employee on that admin's team, reject an assignment to another team's employee, and complete superuser assignments across teams. | Draft |
| SR-INT-003 | Make source-backed knowledge from all scraped documents available to signed-in employees and admins through the registered company chatbot's MCP connection in its first iteration. | Company chatbot; UC-05 | First chatbot iteration | Request knowledge from two teams through the chatbot and inspect sources; deny a signed-out request. | Draft |
| SR-INT-006 | Send team invitation emails through Mailgun to the intended recipient. | Invitation email; UC-07; SOW milestone 1 | Prototype | Initiate an invitation and confirm delivery to the test recipient. | Draft |
| SR-INT-007 | Let an invitation recipient accept the invitation and choose a username and password. | Invitation acceptance; UC-08; SOW milestone 1 | Prototype | Complete an invitation and verify account creation. | Draft |
| SR-INT-008 | Let the Django superuser initiate an invitation to any team, and let a team admin initiate an invitation only to a team they administer. | Admin interface; UC-07; SOW milestone 1 | Prototype | Initiate invitations to two teams as superuser; as team admin, invite to an administered team and verify another team cannot be selected. | Draft |
| SR-INT-009 | Let the Django superuser appoint a team admin through the admin interface. | Admin interface; UC-10; SOW milestone 1 | Prototype | Appoint an admin for a team through the interface and verify that a team admin cannot do so. | Draft |
