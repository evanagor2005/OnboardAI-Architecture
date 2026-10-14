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
| Employee interface | Signed-in employee associated with a team | Request and follow a team or individually assigned path | Employee identity, request, team or assignment | Path with source references, or an unavailable/denied result | Prototype |
| Admin interface | Signed-in admin | Create a team and assign an individual topic | Admin identity, team details or employee and topic | Confirmation or failure | Prototype |
| Company chatbot through MCP | Signed-in employee or admin using the chatbot | Retrieve permitted onboarding knowledge | Verified requester identity and question | Permitted source-backed content, or unavailable/denied result | Prototype; registration dependency |
| Documentation ingestion | Connected documentation sources | Supply team knowledge | Source content and team association | Indexed knowledge or ingestion failure | Prototype |

## Shall statements

| ID | The system shall... | Interface / use case | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| SR-INT-001 | Let a signed-in employee associated with a team request an onboarding path through the employee interface. | Employee interface; UC-02 | Prototype | Request a path as a software employee and as an employee of another team. | Draft |
| SR-INT-002 | Let an admin create a team and assign an individual topic through the admin interface. | Admin interface; UC-01, UC-03 | Prototype | Complete both tasks as an admin. | Draft |
| SR-INT-003 | Make permitted, source-backed knowledge available to signed-in employees and admins through the registered company chatbot's MCP connection. | Company chatbot; UC-05 | Prototype | Ask the chatbot as an employee and as an admin; inspect sources and access behavior. | Draft |
