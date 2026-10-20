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
| Employee interface | Signed-in employee associated with one invited team | Open available published team paths and assigned Projects, follow steps, open linked original sources, and track or complete progress | Employee account, team association, path or Project assignment, step progress, completion action | Resumable paths and Projects, accessible source references, relevant change or freshness notices, completion record, later general change warning, or unavailable/denied result | Prototype |
| Admin interface | Signed-in team admin or Django superuser | Create teams as superuser, appoint team admins within the allowed scope, invite people, generate and review paths, publish team paths, set team-path audiences, and review Projects for each employee assignment | Admin identity, team, keyword, audience, recipient, and appointment details | Draft preview, source references, publication or assignment confirmation, or failure | Prototype |
| Company chatbot through MCP | Signed-in employee or admin | Retrieve onboarding knowledge from scraped documents | Question and signed-in user identity | Source-backed content from any scraped document, or an unavailable or denied result | First chatbot iteration; registration dependency |
| Documentation ingestion | Connected documentation sources | Supply the common indexed document pool | Source content, identity, reference, and timestamps | Indexed knowledge or ingestion failure | Prototype |
| Team invitation email | Django superuser or admin of destination team, invitation recipient, and Mailgun | Send and accept an invitation to a specific team | Recipient email and destination team | Invitation email or delivery failure; acceptance flow | Prototype; milestone 1 |

## Shall statements

| ID | The system shall... | Interface / use case | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| SR-INT-001 | Show a signed-in employee the published team paths available through team membership and each path's audience, plus Projects explicitly assigned to the employee. | Employee interface; UC-02, UC-04 | Prototype | Compare path lists for assigned and unassigned teammates and open two assigned Projects. | Draft — reconciled with team decision |
| SR-INT-002 | Let authorized admins generate and review team paths before first publication, choose team-path audiences, and review a Project before each employee assignment becomes visible through the admin interface. | Admin interface; UC-01, UC-03, UC-06 | Prototype | Generate and review a team path, publish it, select its audience, review the same Project for two separate employee assignments, and reject unauthorized actions. | Draft — reconciled with team decision |
| SR-INT-003 | Make source-backed knowledge from all scraped documents available to signed-in employees and admins through the registered company chatbot's MCP connection in its first iteration. | Company chatbot; UC-05 | First chatbot iteration | Request knowledge from two teams through the chatbot and inspect sources; deny a signed-out request. | Draft |
| SR-INT-013 | Let an employee open every original-source link included in a team path or Project assigned to that employee. | Employee interface; team decision | Prototype | Assign a path whose sources come from the common document pool, sign in as its employee, and open each linked original document. | Team-confirmed |
| SR-INT-006 | Send team invitation emails through Mailgun to the intended recipient. | Invitation email; UC-07; SOW milestone 1 | Prototype | Initiate an invitation and confirm delivery to the test recipient. | Draft |
| SR-INT-007 | Let an invitation recipient accept the invitation and choose a username and password. | Invitation acceptance; UC-08; SOW milestone 1 | Prototype | Complete an invitation and verify account creation. | Draft |
| SR-INT-008 | Let the Django superuser initiate an invitation to any team, and let a team admin initiate an invitation only to a team they administer. | Admin interface; UC-07; SOW milestone 1 | Prototype | Initiate invitations to two teams as superuser; as team admin, invite to an administered team and verify another team cannot be selected. | Draft |
| SR-INT-009 | Let the Django superuser appoint an admin for any team and an appointed team admin appoint another admin for an administered team through the admin interface. | Admin interface; UC-10; SOW milestone 1 | Prototype | Appoint an admin as superuser; appoint another admin to an administered team as team admin; reject a team-admin appointment to another team. | Draft |
| SR-INT-010 | Through the employee interface, show updates to an active onboarding or assigned learning path and direct the employee to revisit a changed step they had already completed. | Employee interface; UC-11 | Prototype | Change a completed source-backed step in each path type and inspect the revisit notice. | Draft |
| SR-INT-011 | When a documentation refresh fails, keep the active path visible with a freshness warning in the employee interface. | Employee interface; UC-11 | Prototype | Simulate a failed refresh and inspect the path and warning. | Draft |
| SR-INT-012 | Show an employee a caution in the interface when source material associated with a finished path later changes. | Employee interface; SR-FUNC-032 | Prototype | Finish a path, change an associated source, and inspect the affected employee's caution. | Draft — identification method deferred |
