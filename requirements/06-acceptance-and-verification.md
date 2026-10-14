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
| AC-03 | A team admin can assign an employee on that admin's team a documented topic; that employee can access the resulting learning path and its source content, including another team's documents when explicitly assigned, without granting the same access to other employees or ordinary team onboarding. | SR-FUNC-006, SR-FUNC-007, SR-DATA-008, SR-SEC-002, SR-SEC-003, SR-SEC-011, SR-SEC-012 | Cross-team topic assignment and path demonstration for an employee on the admin's team; source access for that employee, denial for another employee and ordinary team onboarding, and denied employee and cross-team admin assignment attempts. | Draft |
| AC-04 | Signed-in employees and admins can use the first company-chatbot integration to retrieve source-backed knowledge from any scraped document, regardless of its team label; signed-out users cannot. | SR-FUNC-008, SR-DATA-007, SR-SEC-001, SR-SEC-004, SR-INT-003 | Chatbot questions from signed-in employee and admin accounts retrieving documents from two teams with source references, plus a denied signed-out request. | Draft |
| AC-05 | A second documentation source can be ingested, and changed or removed content is reflected after refresh. | SR-DATA-002, SR-DATA-004 | Ingestion and update/removal demonstration using both source types. | Draft |
| AC-06 | Human testing produces evidence for onboarding speed, knowledge retention, and knowledge application. | Statement-of-work outcomes | Evaluation results using the measures and targets defined in the design evaluation plan. | Draft |
| AC-07 | An employee's account is associated with exactly one team through an accepted invitation, with no employee team picker. | SR-FUNC-010, SR-FUNC-014, SR-SEC-007 | Accept an invitation, inspect account association, and verify the employee interface has no team-selection action. | Draft |
| AC-08 | Team onboarding uses the employee's invited-team knowledge and company-wide shared knowledge. | SR-DATA-005, SR-DATA-006 | Representative team and shared documents appear in the employee's path while another team's documents do not. | Draft |
| AC-09 | A generated learning path contains ordered steps, each with a summary and a working source link. | SR-FUNC-012, SR-DATA-003 | Inspect generated team and individual-topic paths and open their source links. | Draft |
| AC-10 | The Django superuser can invite someone to any team, while a team admin can invite someone only to a team they administer. An invitation goes through Mailgun; the recipient accepts, chooses credentials, and receives an account associated with the invited team. | SR-FUNC-013, SR-FUNC-014, SR-FUNC-016, SR-INT-006, SR-INT-007, SR-INT-008, SR-SEC-007, SR-SEC-008, SR-SEC-009 | Superuser invitations to two teams, a team admin invitation to an administered team, a rejected cross-team admin invitation, delivery and acceptance, and the created account's team. | Draft — milestone 1 |
| AC-11 | An employee cannot switch teams directly; a transfer succeeds after an invitation from the destination team's admin or the superuser and the employee's acceptance. | SR-FUNC-015, SR-SEC-006 | Failed direct-change attempt and completed authorized invited transfer. | Draft — phase open |
| AC-12 | The Django superuser appoints a team admin; that account can invite people to its team but cannot appoint another team admin. | SR-FUNC-017, SR-SEC-008, SR-SEC-010, SR-INT-009 | Superuser appointment, an accepted team-admin invitation, and a denied appointment attempt by the team admin. | Draft — milestone 1 |

## Requirement coverage

| Requirement ID | Verification method | Test or review case | Planned evidence | Status |
| --- | --- | --- | --- | --- |
