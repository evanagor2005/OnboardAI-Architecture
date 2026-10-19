# Architecture rules — system boundaries

## Questions

- Which responsibilities belong to OnboardAI, source systems, users, and external services?
- What data or commands may cross each boundary?
- Where shall identity and permission context enter and remain available?
- Which boundaries must remain explicit even if components are combined in the prototype?
- What behavior is required when a dependency is unavailable?

## Shall statements

| ID | The architecture shall... | Source requirement ID | Applies to | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| AR-SYS-001 | Keep the employee interface, admin interface, and company-chatbot MCP interface as identifiable system boundaries so each can apply its required behavior and access policy. | SR-SEC-001, SR-SEC-002, SR-SEC-004, SR-INT-001, SR-INT-002, SR-INT-003 | Interface and authorization components | Trace representative requests through each interface and verify the distinct access results. | Draft — derived |
| AR-SYS-002 | Preserve signed-in identity, team association, and any explicit assignment context from the entry point through every protected knowledge request. | SR-FUNC-010, SR-SEC-001, SR-SEC-002, SR-SEC-011 | Interfaces, authorization, retrieval | Trace ordinary onboarding, assigned learning, and MCP requests to their final access decision. | Draft — derived |
| AR-SYS-003 | Separate acquisition of source content from its shared downstream representation so the GitHub and website or wiki sources can supply knowledge without changing the path and retrieval contracts. | SR-DATA-002, SR-DATA-003, SR-DATA-004 | Source connectors, ingestion, retrieval | Ingest both source types and trace their content through the same path and citation behavior. | Draft — derived |
| AR-SYS-004 | Keep source-refresh failure from removing an employee's existing active path. | SR-FUNC-031, SR-INT-011 | Ingestion, path service, employee interface | Simulate a failed refresh and verify the active path remains available with a freshness warning. | Draft — derived |

## Open questions

| Question | Evidence needed | Owner | Status |
| --- | --- | --- | --- |
