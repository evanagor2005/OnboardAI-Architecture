# Architecture rules — interfaces and operations

## Questions

- What information and policy checks shall be consistent across user, admin, and MCP interfaces that are in scope?
- What shall responses expose about source evidence, denial, error, and uncertainty?
- What shall be logged or measured to diagnose failures and prove compliance with requirements?
- How shall secrets, private data, and logs be protected?
- What recovery, backup, cost, and deployment safeguards shall the architecture provide?
- How shall changes be checked before release?

## Shall statements

| ID | The architecture shall... | Source requirement ID | Applies to | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| AR-OPS-001 | Expose the employee's topic choices, active paths, progress, source links, change notices, freshness warnings, and completion result through the employee interface as applicable. | SR-INT-001, SR-INT-010, SR-INT-011, SR-INT-012, SR-FUNC-027, SR-FUNC-030 | Employee interface | Walk the topic, progress, source-change, failure, and completion journeys. | Draft — derived |
| AR-OPS-002 | Expose only authorized team creation, invitations, team-admin appointment, and individual-topic assignment actions through the admin interface. | SR-FUNC-002, SR-INT-002, SR-INT-008, SR-INT-009 | Admin interface | Exercise each action as team admin, superuser, and unauthorized actor. | Draft — derived |
| AR-OPS-003 | Deliver authorized team invitations through Mailgun and carry the invited team, single-use state, and expiration into account creation or transfer. | SR-FUNC-013, SR-FUNC-014, SR-FUNC-015, SR-INT-006, SR-INT-007, SR-SEC-014 | Invitation service and email boundary | Send, accept, reuse, and expire test invitations; inspect account or transfer team. | Draft — derived from the team's Mailgun requirement |
| AR-OPS-004 | Expose source-backed retrievable knowledge to the registered company chatbot through MCP under the first-iteration chatbot access policy, and return an unavailable or denied result when appropriate. | SR-FUNC-008, SR-INT-003, SR-SEC-001, SR-SEC-004 | MCP interface | Ask through the registered chatbot as signed-in users, then test signed-out and unavailable cases. | Draft — derived; chatbot registration capability to verify |
| AR-OPS-005 | Preserve an active path during a failed documentation refresh and visibly mark its knowledge as potentially stale. | SR-FUNC-031, SR-INT-011 | Refresh process and employee interface | Simulate refresh failure and inspect path availability and warning. | Draft — derived |
| AR-OPS-006 | Support verification of onboarding speed, knowledge retention, and knowledge application using project-team-approved real documents or realistic sample documents. | SR-DATA-009; SOW outcomes; AC-06 | Evaluation instrumentation and test environment | Review evaluation corpus approval and collect the measures defined in the evaluation plan. | Draft — derived; targets belong in design |
