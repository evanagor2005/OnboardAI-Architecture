# API and MCP design

Include MCP only if it is in the accepted prototype scope.

## Questions

- What operations are needed between components and external clients?
- What input, output, citation, denial, and error contract does each operation expose?
- How is identity and permission context carried across each boundary?
- Which MCP tools are included, and what may each return?
- How are contracts versioned and tested?

## Contract inventory

| API or tool | Caller | Input | Output | Authorization | Error / denial behavior | Requirement / rule |
| --- | --- | --- | --- | --- | --- | --- |
| Company-chatbot MCP knowledge operation; tool name and schema open | Company chatbot acting for a signed-in employee or admin | Per-user token at the connection boundary; knowledge request in the tool call | Source-backed knowledge and citations; exact response contract open | Separate MCP service verifies the user token and applies the first-iteration all-scraped-documents chatbot policy | Deny missing or invalid user token before knowledge retrieval; unavailable result on service failure | AR-SYS-001–002; SR-FUNC-008, SR-SEC-001, SR-SEC-004, SR-INT-003 |

## Chosen approach and rationale

**Team design:** Run MCP as a separate service using the official Python MCP SDK with Streamable HTTP, initially in a container managed by Docker Compose. The company chatbot connects directly using a token for the signed-in user; MCP verifies it before serving protected tools. The service uses OnboardAI's shared retrieval and authorization behavior, with the approved first-iteration chatbot access policy. Exact tools, host platform, and token issuer remain open. Compatibility and per-user authentication with the intended Claude and OpenAI clients remain to be tested. The MCP service exposes tools; any chatbot agent behavior belongs to its host, while OnboardAI's path-generation workflow is a separate design concern.

**Serious alternatives and tradeoffs:** The team chose direct per-user token access over a Django gateway that forwards each chatbot request. Separate hosting provides an independent MCP endpoint and adds token verification, networking, and deployment work.

**Sequence diagrams:** Chatbot obtains user token → calls MCP → MCP verifies token → authorization determines chatbot scope → retrieval returns source-backed result. Draw the detailed sequence after choosing the chatbot and issuer.

**Verification / open questions:** Prove that each intended Claude and OpenAI client supports the Streamable HTTP endpoint and sends a distinct user token. Test two users and rejected missing, expired, or invalid tokens. Confirm registration and OAuth account linking with the selected clients. Check each chatbot's own conversation-retention behavior; OnboardAI does not retain those questions or answers.
