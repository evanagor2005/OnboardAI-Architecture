# Knowledge and data requirements

## Questions

- Which kinds of knowledge and source systems are included in the prototype?
- What source identity, location, version, owner, and date shall users or evaluators be able to inspect?
- How shall content additions, changes, removals, and permission changes affect results?
- What shall users see when sources conflict, are stale, or cannot be reached?
- What user, conversation, progress, and evaluation data shall be stored or deleted?
- What data volume and update frequency must the prototype handle?

## Shall statements

| ID | The system shall... | Use case / SOW item | Prototype or future | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| SR-DATA-001 | Associate ingested knowledge with its source and the team or teams to which it applies. | SOW milestones 1 and 3 | Prototype | Inspect indexed examples from two teams and trace them to their sources. | Draft |
| SR-DATA-002 | Ingest knowledge from the initial documentation source and a second, different type of documentation source. | SOW milestones 1 and 5 | Prototype | Ingest representative documents from both sources. | Draft |
| SR-DATA-003 | Preserve source references for content used in onboarding and individual-topic paths. | UC-02, UC-04; SOW milestones 2 and 7 | Prototype | Trace path items back to their documents. | Draft |
| SR-DATA-004 | Reflect changed or removed source documents in retrievable knowledge after the agreed refresh process. | SOW milestone 5 | Prototype | Change and remove test documents, refresh, and inspect retrieval results. | Draft — refresh timing open |
| SR-DATA-005 | Distinguish team-specific knowledge from company-wide shared knowledge. | UC-02, UC-05; SOW milestones 3, 4, and 6 | Prototype | Inspect representative team and shared documents after ingestion. | Draft |
| SR-DATA-006 | Use knowledge for the employee's associated team together with company-wide shared knowledge when creating team onboarding paths. | UC-02; SOW milestone 4 | Prototype | Request a path using both team and shared examples, with another team's content absent. | Draft |
| SR-DATA-007 | Make all scraped documents available for retrieval by signed-in employees and admins through the first company-chatbot MCP integration, regardless of team labels. | UC-05; SOW milestone 6 | First chatbot iteration | Ask for documents from two teams and inspect retrieved results and sources. | Draft |

## Data inventory

| Data category | Source / owner | Sensitivity | Retention or deletion need | Scope |
| --- | --- | --- | --- | --- |
