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
| SR-DATA-002 | Ingest documentation files from a GitHub repository first, then add a website or wiki as a second source. | SOW milestones 1 and 5 | Prototype | Ingest representative documents from the repository and website or wiki and trace results to both. | Draft |
| SR-DATA-003 | Preserve source references for content used in onboarding and individual-topic paths. | UC-02, UC-04; SOW milestones 2 and 7 | Prototype | Trace path items back to their documents. | Draft |
| SR-DATA-004 | Reflect changed or removed source documents in retrievable knowledge after the agreed refresh process. | SOW milestone 5 | Prototype | Change and remove test documents, refresh, and inspect retrieval results. | Draft — refresh timing open |
| SR-DATA-005 | Distinguish team-specific knowledge from company-wide shared knowledge. | UC-02, UC-05; SOW milestones 3, 4, and 6 | Prototype | Inspect representative team and shared documents after ingestion. | Draft |
| SR-DATA-006 | Use knowledge for the employee's associated team together with company-wide shared knowledge when creating team onboarding paths. | UC-02; SOW milestone 4 | Prototype | Request a path using both team and shared examples, with another team's content absent. | Draft |
| SR-DATA-007 | Make all scraped documents available for retrieval by signed-in employees and admins through the first company-chatbot MCP integration, regardless of team labels. | UC-05; SOW milestone 6 | First chatbot iteration | Ask for documents from two teams and inspect retrieved results and sources. | Draft |
| SR-DATA-008 | Permit an individually assigned learning path to use relevant hub documents from another team when the employee's explicit assignment grants access to them. | UC-04; SOW milestone 7 | Prototype | Assign a cross-team topic, open the resulting path as the assigned employee, and inspect its document references. | Draft |
| SR-DATA-009 | Use only approved real documents or realistic sample documents in the prototype's evaluation content. | SOW milestone 9 | Prototype | Review the evaluation corpus and approval record for each real document. | Draft — approval process open |

## Data inventory

| Data category | Source / owner | Sensitivity | Retention or deletion need | Scope |
| --- | --- | --- | --- | --- |
| Approved real documentation | GitHub repository or website/wiki; owner to identify | To classify before use | To define | Prototype evaluation |
| Realistic sample documentation | Created by the project team | To define | To define | Prototype evaluation |
