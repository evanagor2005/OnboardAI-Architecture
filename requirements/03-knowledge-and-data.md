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
| SR-DATA-002 | Ingest Markdown documentation files from a public GitHub repository first, then add a website or wiki as a second source. | SOW milestones 1 and 5 | Prototype | Ingest Markdown files from the public repository and pages from the website or wiki, then trace results to both sources. | Draft — website/wiki access chosen with source |
| SR-DATA-003 | Preserve source references for documentation-backed content used in onboarding and individual-topic paths. | UC-02, UC-04; SOW milestones 2 and 7 | Prototype | Trace documented path items back to their source documents and distinguish AI-inferred items. | Draft |
| SR-DATA-004 | Reflect changed or removed GitHub source files in retrievable knowledge after the 10-minute polling and refresh process beginning in milestone 2; reflect changed or removed website or wiki pages after the agreed refresh process beginning in milestone 5. | SOW milestones 2 and 5 | Prototype | Change and remove test content from each source, refresh, and inspect retrieval results. | Draft — website/wiki refresh schedule chosen with source |
| SR-DATA-005 | Distinguish team-specific knowledge from company-wide shared knowledge. | UC-02, UC-05; SOW milestones 3, 4, and 6 | Prototype | Inspect representative team and shared documents after ingestion. | Draft |
| SR-DATA-006 | Use knowledge for the employee's associated team together with company-wide shared knowledge when creating team onboarding paths, or use shared knowledge alone when that team has no team-specific onboarding documents. | UC-02; SOW milestone 4 | Prototype | Request paths with team and shared examples, then for a team with shared material only; verify another team's content stays absent. | Draft |
| SR-DATA-007 | Make all scraped documents available for retrieval by signed-in employees and admins through the first company-chatbot MCP integration, regardless of team labels. | UC-05; SOW milestone 6 | First chatbot iteration | Ask for documents from two teams and inspect retrieved results and sources. | Draft |
| SR-DATA-008 | Permit an individually assigned learning path to use relevant hub documents from another team when the employee's explicit assignment grants access to them. | UC-04; SOW milestone 7 | Prototype | Assign a cross-team topic, open the resulting path as the assigned employee, and inspect its document references. | Draft |
| SR-DATA-009 | Use only project-team-approved real documents or realistic sample documents in the prototype's evaluation content. | SOW milestone 9 | Prototype | Review the evaluation corpus and project-team approval record for each real document. | Draft — approval recording method open |
| SR-DATA-010 | Poll the public GitHub documentation repository every 10 minutes for added, changed, and removed Markdown files beginning in milestone 2. | SOW milestone 2 | Prototype | Add, change, and remove test Markdown files, wait for the next 10-minute polling cycle, and inspect indexed knowledge. | Draft |
| SR-DATA-011 | Retain each ingested document's creation or last-updated timestamp with its source reference so conflicting documents can be dated in generated results. | UC-02, UC-05 | Prototype | Inspect indexed documents with known dates and check the dates in a conflicting-source result. | Draft — tested sources assumed dated |
| SR-DATA-012 | Keep each generated onboarding or assigned learning path and its completed-step state across sign-ins while in progress. After completion, retain a record identifying the employee and completed path; delete the generated path content and step details. | UC-11, UC-12; SOW milestones 2 and 7 | Prototype | Resume both path types after sign-in; finish them; verify the employee-to-path completion record remains while generated content and step details are deleted. | Draft — updated by team decision |
| SR-DATA-013 | Use documentation relevant to a team's derived onboarding topic when generating that topic's path, while applying the employee-interface document access rules. | UC-02; SR-FUNC-028; SOW milestone 2 | Prototype | Compare Software Database and API paths and confirm each uses relevant permitted sources. | Draft |
| SR-DATA-014 | Do not retain company-chatbot questions or answers in OnboardAI's data store. | UC-05; SOW milestone 6 | First chatbot iteration | Use the chatbot, then inspect OnboardAI's stored data for the question and answer. | Draft |

## Data inventory

| Data category | Source / owner | Sensitivity | Retention or deletion need | Scope |
| --- | --- | --- | --- | --- |
| Approved real documentation | Public GitHub Markdown repository or website/wiki; owner to identify | To classify before use | To define | Prototype evaluation |
| Realistic sample documentation | Created by the project team | To define | To define | Prototype evaluation |
| Active onboarding or assigned learning path and completed-step state | Employee request and activity; system-generated content | To classify | Keep across sign-ins while in progress; delete generated path content and step details after completion | Prototype |
| Completion record | Employee and completed path | To classify | Keep the employee-to-completed-path record; exact fields and retention period to define in design | Prototype |
| Company-chatbot questions and answers | Company chatbot | To classify | Do not retain in OnboardAI | First chatbot iteration |

**Completion-change caution:** The team decided to retain a record of the employee and path they completed while deleting generated path content and steps. It has deferred whether any source association is needed to identify affected employees after later source changes. No per-step completion history or completion-to-source association has been approved for finished paths.

**Prototype corpus assumption:** Each tested role and assigned topic has at least some relevant documentation. For team onboarding, company-wide shared material satisfies this assumption when the team has no team-specific onboarding documents. Sources used to demonstrate conflicting information provide a creation or last-updated timestamp. A request with no relevant source documents at all is outside the agreed evaluation scenario; behavior for that case remains undecided.
