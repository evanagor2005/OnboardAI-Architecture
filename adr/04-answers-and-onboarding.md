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
| AR-LEARN-002 | Generate and save a reusable Project from an admin-supplied keyword before assignment, then reuse its published content for multiple employees with separate progress. | SR-FUNC-006, SR-FUNC-007, SR-FUNC-023, SR-FUNC-033 | Project creation and assignment | Assign one published Project to two employees and verify the same saved steps with independent progress. | Draft — reconciled |
| AR-LEARN-003 | Produce ordered path steps with summaries, working source references for documented steps, and no fabricated source attribution for AI-suggested steps. | SR-FUNC-012, SR-FUNC-019, SR-FUNC-021, SR-DATA-003 | Path generation and presentation | Inspect steps, open links, and test documented and undocumented cases. | Draft — derived |
| AR-LEARN-004 | Identify an AI-inferred missing step as an inference and present multiple plausible missing steps as labeled alternatives rather than documented facts. | SR-FUNC-019, SR-FUNC-021 | Path generation and presentation | Run obvious-gap and ambiguous-gap cases for both path types. | Draft — derived; obvious-step criterion open in design |
| AR-LEARN-005 | Present conflicting documented accounts neutrally with a source reference and creation or last-updated timestamp for each. | SR-FUNC-020, SR-DATA-011 | Retrieval and response presentation | Use conflicting dated documents and inspect path and chatbot outputs. | Draft — derived |
| AR-LEARN-006 | Let an authorized admin use relevant common-pool documents to create a path for a team, including documents already used by another team's path; do not infer source ownership from path ownership. | SR-FUNC-005, SR-DATA-005, SR-DATA-006 | Team-path generation and provenance | Use one source in paths for two teams and verify both original-source links remain valid. | Draft — replaces obsolete shared-only fallback |
| AR-LEARN-007 | Revise a shared published path or Project when a relevant source change conflicts with it; direct each active employee to revisit an affected completed step while updating future steps without a notice. | SR-FUNC-025, SR-FUNC-026, SR-INT-010 | Source-change processing, shared definitions, active progress | Have two employees at different steps of one saved path, change supporting material, and inspect their respective notices and updated steps. | Draft — reconciled |
| AR-LEARN-008 | For Project generation, search the full indexed documentation pool when no team filter is supplied; when a team filter is supplied, narrow to documents relevant to that team while retaining company-wide material. Treat the filter as search context, not document ownership, Project ownership, or employee assignment. | SR-FUNC-033; team decision | Project generation and retrieval | Generate Projects from the same keyword with no filter and with a Software filter; inspect relevant source references and verify that the Project remains team-independent. | Accepted — scope decided; filter method open |
| AR-LEARN-009 | Require admin review before a newly generated Project is first published, then publish successful source-driven revisions of an already published Project without requiring another admin review. | SR-FUNC-033; team decision | Project generation, review, and refresh | Generate a Project and verify employees cannot see it before admin approval; change a supporting source and verify the successful revision becomes available without a second approval. | Accepted — team decision |
