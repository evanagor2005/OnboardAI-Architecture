# Identity and access design

## Questions

- How are users and software clients identified and authenticated?
- Where does permission information come from, and when is it refreshed?
- Where is policy evaluated and enforced on each data and answer path?
- How do included interfaces receive the same access outcome?
- What happens when identity or policy data is unavailable?
- What access events are logged, and how are those logs protected?

## Protected flows

| Flow | Identity source | Policy input | Enforcement point | Allowed output | Denied / failure output | Test case |
| --- | --- | --- | --- | --- | --- | --- |
| Company chatbot to separate MCP service | A per-user token from a trusted issuer; issuer and chatbot token flow to select | Verified user identity and the first-iteration MCP policy | MCP token-verification boundary, then OnboardAI authorization before retrieval | Source-backed knowledge from all scraped documents for a signed-in employee or admin | Deny missing, invalid, expired, or unrecognized user tokens; return an unavailable result if retrieval fails | Use two signed-in users, an unsigned request, and invalid/expired tokens; verify identity reaches authorization and results follow the MCP policy |
| Team admin managing another team | Signed-in user with a team-admin appointment for the target team | Team-admin appointment for path and linked-source review; the user's own employee team for employee paths | Admin interface path/source checks and employee "My Paths" authorization checks | Admin may manage/review the target team's paths and open linked source documents in the admin interface; employee list shows only paths assigned through the user's own team | Deny target-team admin review without appointment; do not treat an appointment as employee-path assignment | Make a Software employee an HR admin; open an HR path and linked source in admin view, then verify HR paths remain absent from employee "My Paths" |
| Shared Project assignment | Signed-in team admin or Django superuser | Admin's appointment for the recipient employee's team, or superuser authority; Project creator's team is not an access limit | Admin assignment action | HR admin may review and assign a Software-created Project to an HR employee; the employee sees it after that review, with separate progress | Deny a team admin's assignment to an employee outside that admin's administered teams | Assign one Project created by a Software admin to HR and Software employees using authorized admins; reject an unauthorized employee target |
| Project creation and source review | Signed-in team admin or Django superuser | Admin role; Project generation searches the full pool | Admin Project creation and review actions, before source content is shown | Admin may search the common index and inspect linked original sources | Deny non-admin creation or review; do not add the Project to an unassigned employee's path list | Generate and review a Project using a source also used in another team's path; verify only assignees see the Project |

## Chosen approach and rationale

**Team design:** The MCP server runs separately from the Django web application. The company chatbot connects directly with a token representing its signed-in user. The MCP service verifies that token on each protected request and passes the resulting user identity to OnboardAI's authorization logic. Django is the selected account and web-login system, including the milestone-1 invitation flow; Keycloak is not selected. The hosted-chatbot OAuth account-linking method, issuer, token claims, token acquisition flow, and verification mechanism remain open. The MCP policy differs from ordinary employee-interface retrieval in the first chatbot iteration. Team-admin appointments permit path management and review, including opening linked source documents, through the admin interface for every administered team; they do not add those paths to the admin's employee "My Paths" list. Projects are available for assignment across teams; assignment authority is checked against the recipient employee's team, not the Project creator's team.

**Project review decision:** For this prototype, the team assumes indexed documentation is not confidential. A team admin may inspect common-pool documents while creating or reviewing a Project. Each Project assignment becomes visible in the employee interface only after its assigning admin reviews the Project for that employee; the assignee can then open every linked original source. An admin's ability to review another team's path does not add that path to the admin's employee list. Project generation has no team filter; its source references do not confer employee access.

**Serious alternatives and tradeoffs:** The team chose direct per-user tokens over relaying every chatbot request through a Django authentication gateway. This removes the gateway hop but requires the selected chatbot to support per-user token delivery and the MCP service to verify tokens independently.

**Trust-boundary diagram:** Company chatbot → per-user token → MCP verification → OnboardAI authorization → permitted knowledge. The MCP endpoint must not treat a user ID or team supplied as an ordinary tool argument as proof of identity.

**Verification / open questions:** Confirm the selected chatbot can obtain and send a token for each signed-in user. Select the trusted token issuer and decide how MCP validates issuer, intended audience, expiration, and user identity. Test missing, invalid, expired, and wrong-user tokens before registering the chatbot. Decide how Django's account identity maps to token identity. The identity and access architecture rules remain drafts until the team reviews them.
