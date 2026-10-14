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
| AC-02 | Employees on two teams receive distinct paths without restricted cross-team content. | SR-FUNC-005, SR-SEC-002 | Two representative accounts, their generated paths, and an access-denial check. | Draft |
| AC-03 | An admin can assign one employee a documented topic; that employee can access the resulting learning path. | SR-FUNC-006, SR-FUNC-007, SR-SEC-003 | Admin assignment and employee path demonstration; employee assignment attempt denied. | Draft |
| AC-04 | Signed-in employees and admins can use the company chatbot to access only permitted, source-backed knowledge. | SR-FUNC-008, SR-SEC-004, SR-INT-003 | Chatbot questions from representative employee and admin accounts, including a restricted-content case. | Draft |
| AC-05 | A second documentation source can be ingested, and changed or removed content is reflected after refresh. | SR-DATA-002, SR-DATA-004 | Ingestion and update/removal demonstration using both source types. | Draft |
| AC-06 | Human testing produces evidence for onboarding speed, knowledge retention, and knowledge application. | Statement-of-work outcomes | Evaluation results using the measures and targets defined in the design evaluation plan. | Draft |

## Requirement coverage

| Requirement ID | Verification method | Test or review case | Planned evidence | Status |
| --- | --- | --- | --- | --- |
