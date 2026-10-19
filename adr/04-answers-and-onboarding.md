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
| AR-LEARN-001 | Derive selectable team topics from ingested, permitted documentation and generate a distinct path for the selected topic when the employee requests it. | SR-FUNC-004, SR-FUNC-028, SR-FUNC-029, SR-DATA-013, SR-INT-001 | Topic discovery, path generation | Ingest Software Database and API documents, choose each derived topic, and compare resulting paths and sources. | Draft — derived |
| AR-LEARN-002 | Generate an assigned-topic path when its assigned employee opens it, using relevant content authorized for that assignment. | SR-FUNC-006, SR-FUNC-007, SR-FUNC-023, SR-DATA-008 | Assignment and path generation | Assign and open a documented topic, including a permitted cross-team example. | Draft — derived |
| AR-LEARN-003 | Produce ordered path steps with summaries, working source references for documented steps, and no fabricated source attribution for AI-suggested steps. | SR-FUNC-012, SR-FUNC-019, SR-FUNC-021, SR-DATA-003 | Path generation and presentation | Inspect steps, open links, and test documented and undocumented cases. | Draft — derived |
| AR-LEARN-004 | Identify an AI-inferred missing step as an inference and present multiple plausible missing steps as labeled alternatives rather than documented facts. | SR-FUNC-019, SR-FUNC-021 | Path generation and presentation | Run obvious-gap and ambiguous-gap cases for both path types. | Draft — derived; obvious-step criterion open in design |
| AR-LEARN-005 | Present conflicting documented accounts neutrally with a source reference and creation or last-updated timestamp for each. | SR-FUNC-020, SR-DATA-011 | Retrieval and response presentation | Use conflicting dated documents and inspect path and chatbot outputs. | Draft — derived |
| AR-LEARN-006 | Generate a shared-knowledge onboarding path and state that no team-specific path is available when shared documentation exists but the employee's team has none. | SR-FUNC-022, SR-DATA-006 | Path generation and employee interface | Request a path for a team with shared-only material and inspect the notice and sources. | Draft — derived |
| AR-LEARN-007 | Update an active path when a relevant source change conflicts with it; direct the employee to revisit an affected completed step and update a future step without a notice. | SR-FUNC-025, SR-FUNC-026, SR-INT-010 | Source-change processing, active paths | Change completed and future source-backed steps in both path types and inspect updates and notices. | Draft — derived |
