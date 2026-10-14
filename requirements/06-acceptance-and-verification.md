# Acceptance and verification requirements

Decide what will count as a successful prototype before interpreting test results. The detailed test approach belongs in [`../design/09-evaluation-plan.md`](../design/09-evaluation-plan.md).

## Questions

- Which user journeys must be demonstrated end to end?
- Which requirement and architecture-rule outcomes are acceptance gates?
- How will answer quality, citations, permissions, freshness, and onboarding usefulness be judged?
- What representative roles, content, and failure cases will be used?
- Who reviews results and accepts the prototype?

## Acceptance criteria

| Criterion ID | Required outcome | Linked requirement(s) | Evidence needed | Status |
| --- | --- | --- | --- | --- |
| AC-01 | A software employee can request a dynamically created path with relevant source references. | SR-FUNC-004, SR-DATA-003, SR-SEC-002 | Demonstration of a requested path and its document references. | Draft |
| AC-02 | Employees invited to two teams receive distinct paths without the other team's documents appearing in their employee-interface paths. | SR-FUNC-005, SR-SEC-002 | Two invited accounts, their generated paths, and a cross-team employee-interface check. | Draft |
| AC-03 | An admin can assign one employee a documented topic; that employee can access the resulting learning path. | SR-FUNC-006, SR-FUNC-007, SR-SEC-003 | Admin assignment and employee path demonstration; employee assignment attempt denied. | Draft |
| AC-04 | The first company-chatbot integration can return source-backed knowledge from any scraped document, regardless of its team label. | SR-FUNC-008, SR-DATA-007, SR-SEC-004, SR-INT-003 | Chatbot questions retrieving documents from two teams and checking source references. | Draft — user eligibility open |
| AC-05 | A second documentation source can be ingested, and changed or removed content is reflected after refresh. | SR-DATA-002, SR-DATA-004 | Ingestion and update/removal demonstration using both source types. | Draft |
| AC-06 | Human testing produces evidence for onboarding speed, knowledge retention, and knowledge application. | Statement-of-work outcomes | Evaluation results using the measures and targets defined in the design evaluation plan. | Draft |
| AC-07 | An employee's account is associated with exactly one team through an accepted invitation, with no employee team picker. | SR-FUNC-010, SR-FUNC-014, SR-SEC-007 | Accept an invitation, inspect account association, and verify the employee interface has no team-selection action. | Draft |
| AC-08 | Team onboarding uses the employee's invited-team knowledge and company-wide shared knowledge. | SR-DATA-005, SR-DATA-006 | Representative team and shared documents appear in the employee's path while another team's documents do not. | Draft |
| AC-09 | A generated learning path contains ordered steps, each with a summary and a working source link. | SR-FUNC-012, SR-DATA-003 | Inspect generated team and individual-topic paths and open their source links. | Draft |
| AC-10 | An admin sends an invitation to the admin's own team through Mailgun; the recipient accepts, chooses credentials, and receives an account associated with that team. | SR-FUNC-013, SR-FUNC-014, SR-INT-006, SR-INT-007, SR-INT-008, SR-SEC-007, SR-SEC-008 | Invitation email, acceptance flow, created account, and rejected attempt to invite to another admin's team. | Draft — milestone 1 |
| AC-11 | An employee cannot switch teams directly; a transfer succeeds after a destination-team admin invitation and the employee's acceptance. | SR-FUNC-015, SR-SEC-006 | Failed direct-change attempt and completed invited transfer. | Draft — phase open |

## Requirement coverage

| Requirement ID | Verification method | Test or review case | Planned evidence | Status |
| --- | --- | --- | --- | --- |
