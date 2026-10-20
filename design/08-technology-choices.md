# Technology choices and rationale

Compare products and frameworks only after the relevant requirements, architecture rules, and component design are clear. This file replaces a separate design-decision folder.

## Selection criteria

| Criterion | Requirement / rule | Must-have or preference | Weight / priority | Evidence method |
| --- | --- | --- | --- | --- |

## Choices

| Area | Serious options | Evidence | Selected option | Why it fits / tradeoffs | Revisit trigger | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Client framework |  |  |  |  |  | Open |
| Backend language / framework | Django named by the team for the superuser and invitation account flow |  |  |  |  | Team direction; full backend choice open |
| Database |  |  |  |  |  | Open |
| Search / indexing |  |  |  |  |  | Open |
| AI model / service, if needed |  |  |  |  |  | Open |
| Identity / authorization | Django superuser and invite-created accounts for milestone 1; token issuer and verifier candidates open | Team chose a separate MCP service with direct per-user tokens; selected chatbot capability still to verify | Django accounts for milestone 1; per-user token verification at the MCP boundary | Supports signed-in chatbot access without relaying requests through Django; adds issuer, verification, and identity-mapping work | Revisit if selected chatbot cannot send per-user tokens | Team direction; token technology open |
| Invitation email delivery | Mailgun |  | Mailgun | Team direction; integration evidence pending | If email delivery requirements change | Team choice |
| Source integration |  |  |  |  |  | Open |
| MCP implementation, if included | SDK and transport candidates to research | Team chose separate MCP service and direct per-user tokens; chatbot registration proof pending | Separate MCP service; SDK and transport open | Preserves a distinct chatbot boundary and direct connection | Revisit if selected chatbot cannot connect directly with user identity | Service boundary chosen; implementation open |
| Hosting / deployment | Platform candidates to research | MCP must be reachable by the selected company chatbot; local development arrangement still to choose | MCP hosted separately from Django; platform open | Independent MCP endpoint; network and operational work to evaluate | Revisit with chatbot network requirements | Service separation chosen; platform open |

## Evidence still needed

| Uncertain choice | Small test or research | Pass condition | Owner | Status |
| --- | --- | --- | --- | --- |
| Per-user chatbot token support | Register a test MCP service with the intended company chatbot and make requests as two signed-in users plus a signed-out user. | MCP receives a distinct verifiable user identity for each signed-in request and rejects the signed-out request. | Team to assign | Open |
| Token issuer and verification | Compare issuer options compatible with Django accounts and the chosen chatbot; test valid, expired, wrong-audience, and invalid tokens. | MCP can verify each request and map the token to the intended OnboardAI user without trusting tool arguments. | Team to assign | Open |
