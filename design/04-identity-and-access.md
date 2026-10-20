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
| Team admin managing another team | Signed-in user with a team-admin appointment for the target team | Team-admin appointment for admin actions; the user's own employee team for employee paths | Admin interface and employee "My Paths" authorization checks | Admin may manage/review the target team's paths in the admin interface; employee list shows only paths assigned through the user's own team | Deny target-team admin actions without appointment; do not treat an appointment as employee-path assignment | Make a Software employee an HR admin; show HR paths in HR admin management but not in that employee's "My Paths" list |

## Chosen approach and rationale

**Team design:** The MCP server runs separately from the Django web application. The company chatbot connects directly with a token representing its signed-in user. The MCP service verifies that token on each protected request and passes the resulting user identity to OnboardAI's authorization logic. Django remains the milestone-1 account and web-login system. The issuer, token claims, token acquisition flow, and verification mechanism remain open. The MCP policy differs from ordinary employee-interface retrieval in the first chatbot iteration. Team-admin appointments permit management and review through the admin interface, including for teams other than the admin's employee team; they do not add those paths to the admin's employee "My Paths" list.

**Serious alternatives and tradeoffs:** The team chose direct per-user tokens over relaying every chatbot request through a Django authentication gateway. This removes the gateway hop but requires the selected chatbot to support per-user token delivery and the MCP service to verify tokens independently.

**Trust-boundary diagram:** Company chatbot → per-user token → MCP verification → OnboardAI authorization → permitted knowledge. The MCP endpoint must not treat a user ID or team supplied as an ordinary tool argument as proof of identity.

**Verification / open questions:** Confirm the selected chatbot can obtain and send a token for each signed-in user. Select the trusted token issuer and decide how MCP validates issuer, intended audience, expiration, and user identity. Test missing, invalid, expired, and wrong-user tokens before registering the chatbot. Decide how Django's account identity maps to token identity. The identity and access architecture rules remain drafts until the team reviews them.
