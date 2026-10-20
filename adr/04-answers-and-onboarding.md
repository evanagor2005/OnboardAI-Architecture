# Architecture rules — answers and onboarding

Include only capabilities accepted in the statement of work and software requirements.

## Questions

- What source evidence shall accompany an answer, and how shall it remain inspectable?
- When shall the system abstain, express uncertainty, or surface conflicting sources?
- How shall malicious or misleading source content be prevented from changing system behavior?
- If paths are included, what shall define their role relevance and source basis?
- If progress or assessments are included, what shall be stored, visible, and protected?
- When shall the system direct a learner to a person?

## Shall statements

| ID | The architecture shall... | Source requirement ID | Applies to | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| AR-LEARN-001 | Generate and save reusable team paths from admin-supplied keywords and relevant common-pool evidence; require admin review before first publication and show published paths according to team and audience. | SR-FUNC-004, SR-FUNC-028, SR-FUNC-029, SR-DATA-013, SR-INT-001 | Team-path generation and publication | Generate and review Database and API paths, then compare assigned employees' views and sources. | Draft — reconciled |
| AR-LEARN-002 | Generate and save a reusable Project from an admin-supplied keyword before assignment, then reuse its saved content for multiple employees with separate progress after each assigning admin reviews that employee's assignment. | SR-FUNC-006, SR-FUNC-007, SR-FUNC-023, SR-FUNC-033 | Project creation and assignment | Have two admins review and assign one saved Project to different employees; verify the same saved steps and independent progress. | Draft — reconciled |
| AR-LEARN-003 | Produce ordered path steps with summaries, working source references for documented steps, and no fabricated source attribution for AI-suggested steps. | SR-FUNC-012, SR-FUNC-019, SR-FUNC-021, SR-DATA-003 | Path generation and presentation | Inspect steps, open links, and test documented and undocumented cases. | Draft — derived |
| AR-LEARN-004 | Identify an AI-inferred missing step as an inference and present multiple plausible missing steps as labeled alternatives rather than documented facts. | SR-FUNC-019, SR-FUNC-021 | Path generation and presentation | Run obvious-gap and ambiguous-gap cases for both path types. | Draft — derived; obvious-step criterion open in design |
| AR-LEARN-005 | Present conflicting documented accounts neutrally with a source reference and creation or last-updated timestamp for each. | SR-FUNC-020, SR-DATA-011 | Retrieval and response presentation | Use conflicting dated documents and inspect path and chatbot outputs. | Draft — derived |
| AR-LEARN-006 | Let an authorized admin use relevant common-pool documents to create a path for a team, including documents already used by another team's path; do not infer source ownership from path ownership. | SR-FUNC-005, SR-DATA-005, SR-DATA-006 | Team-path generation and provenance | Use one source in paths for two teams and verify both original-source links remain valid. | Draft — replaces obsolete shared-only fallback |
| AR-LEARN-007 | Revise a published team path or a saved Project when a relevant source change conflicts with it; direct each active employee to revisit an affected completed step while updating future steps without a notice. | SR-FUNC-025, SR-FUNC-026, SR-INT-010 | Source-change processing, shared definitions, active progress | Have two employees at different steps of one saved path, change supporting material, and inspect their respective notices and updated steps. | Draft — reconciled |
| AR-LEARN-008 | For Project generation, search the full indexed documentation pool using the admin-supplied keyword. Do not apply a team filter or infer document ownership from the Project or its assignees. | SR-FUNC-033; team decision | Project generation and retrieval | Generate a Project from a keyword and inspect relevant source references across the full pool; verify that the Project remains team-independent. | Accepted — full-pool search; no team filter |
| AR-LEARN-009 | Require the admin assigning a Project to review it before that employee can see it, even if another admin already reviewed the shared Project for a different employee. After an assignment is visible, make successful source-driven revisions available to its employee without another admin review. | SR-FUNC-033; team decision | Project generation, review, and refresh | Generate one Project; have two admins review it for different employees and verify each assignment remains hidden until its own review. Change a supporting source and verify the successful revision becomes available to existing assignees without another review. | Accepted — team decision |
| AR-LEARN-010 | Give an employee correct or incorrect feedback after a question step, show the correct answer after an incorrect response, and allow progression regardless of the answer. | SR-FUNC-034; team decision | Team paths, Projects, employee interface | Answer question steps correctly and incorrectly in both path types; inspect feedback and continue in each case. | Accepted — team decision |
