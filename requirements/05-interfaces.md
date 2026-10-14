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
| Employee interface | Signed-in employee associated with one invited team | Request and follow a team or individually assigned path | Employee account and team association, path request or assignment | Path with source references, or an unavailable/denied result | Prototype |
| Admin interface | Signed-in team admin | Create a team, invite a person to the admin's team, and assign an individual topic | Admin identity, team and recipient details, or employee and topic | Confirmation or failure | Prototype |
| Company chatbot through MCP | Eligible chatbot user | Retrieve onboarding knowledge from scraped documents | Question; user eligibility rules to define | Source-backed content from any scraped document, or an unavailable result | First chatbot iteration; registration dependency |
| Documentation ingestion | Connected documentation sources | Supply team knowledge | Source content and team association | Indexed knowledge or ingestion failure | Prototype |
| Team invitation email | Admin of destination team, invitation recipient, and Mailgun | Send and accept an invitation to a specific team | Recipient email and destination team | Invitation email or delivery failure; acceptance flow | Prototype; milestone 1 |

## Shall statements

| ID | The system shall... | Interface / use case | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| SR-INT-001 | Let a signed-in employee associated with a team request an onboarding path through the employee interface. | Employee interface; UC-02 | Prototype | Request a path as a software employee and as an employee of another team. | Draft |
| SR-INT-002 | Let an admin create a team and assign an individual topic through the admin interface. | Admin interface; UC-01, UC-03 | Prototype | Complete both tasks as an admin. | Draft |
| SR-INT-003 | Make source-backed knowledge from all scraped documents available through the registered company chatbot's MCP connection in its first iteration. | Company chatbot; UC-05 | First chatbot iteration | Request knowledge from two teams through the chatbot and inspect sources. | Draft — user eligibility open |
| SR-INT-006 | Send team invitation emails through Mailgun to the intended recipient. | Invitation email; UC-07; SOW milestone 1 | Prototype | Initiate an invitation and confirm delivery to the test recipient. | Draft |
| SR-INT-007 | Let an invitation recipient accept the invitation and choose a username and password. | Invitation acceptance; UC-08; SOW milestone 1 | Prototype | Complete an invitation and verify account creation. | Draft |
| SR-INT-008 | Let a team admin initiate an invitation to that team through the admin interface. | Admin interface; UC-07; SOW milestone 1 | Prototype | Initiate an invitation to the admin's team and verify another team cannot be selected. | Draft |
