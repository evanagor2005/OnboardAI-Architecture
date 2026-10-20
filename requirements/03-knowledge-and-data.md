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
| SR-DATA-001 | Keep each ingested item's source identity and reference without deriving exclusive document ownership from the team path that uses it. | SOW milestones 1 and 3 | Prototype | Trace one indexed document to paths for two teams and verify both retain the same source reference. | Draft — reconciled with common-pool decision |
| SR-DATA-002 | Ingest Markdown documentation files from a public GitHub repository first, then add a website or wiki as a second source. | SOW milestones 1 and 5 | Prototype | Ingest Markdown files from the public repository and pages from the website or wiki, then trace results to both sources. | Draft — website/wiki access chosen with source |
| SR-DATA-003 | Preserve source references for documentation-backed content used in onboarding and individual-topic paths. | UC-02, UC-04; SOW milestones 2 and 7 | Prototype | Trace documented path items back to their source documents and distinguish AI-inferred items. | Draft |
| SR-DATA-004 | Reflect changed or removed GitHub source files in retrievable knowledge after the 10-minute polling and refresh process beginning in milestone 2; reflect changed or removed website or wiki pages after the agreed refresh process beginning in milestone 5. | SOW milestones 2 and 5 | Prototype | Change and remove test content from each source, refresh, and inspect retrieval results. | Draft — website/wiki refresh schedule chosen with source |
| SR-DATA-005 | Keep the common indexed documentation pool available as evidence for admin-created paths without making source documents exclusive to a path's team. | UC-06; SOW milestones 2 and 4 | Prototype | Use one relevant document in paths for two teams and inspect both paths' source references. | Draft — reconciled with common-pool decision |
| SR-DATA-006 | Retrieve documentation relevant to an admin-supplied team-path keyword from the common pool and retain original-source references in the generated path. | UC-06; SOW milestones 2 and 4 | Prototype | Generate two different team paths using relevant common-pool documents and inspect their linked sources. | Draft — replaces obsolete shared-only fallback |
| SR-DATA-007 | Make all scraped documents in the common pool available for retrieval by signed-in employees and admins through the first company-chatbot MCP integration. | UC-05; SOW milestone 6 | First chatbot iteration | Ask for documents covering two different team topics and inspect retrieved results and sources. | Draft — reconciled with common-pool decision |
| SR-DATA-008 | Permit a reusable Project to use relevant documents from the common pool, independent of the assignee's team; make its original-source links openable by every assigned employee. | UC-03, UC-04; SOW milestone 7 | Prototype | Assign one Project using common-pool sources to employees on two teams and open each linked source as both assignees. | Draft — reconciled with common-pool decision |
| SR-DATA-009 | Use only project-team-approved real documents or realistic sample documents in the prototype's evaluation content. | SOW milestone 9 | Prototype | Review the evaluation corpus and project-team approval record for each real document. | Draft — approval recording method open |
| SR-DATA-010 | Poll the public GitHub documentation repository every 10 minutes for added, changed, and removed Markdown files beginning in milestone 2. | SOW milestone 2 | Prototype | Add, change, and remove test Markdown files, wait for the next 10-minute polling cycle, and inspect indexed knowledge. | Draft |
| SR-DATA-011 | Retain each ingested document's creation or last-updated timestamp with its source reference so conflicting documents can be dated in generated results. | UC-02, UC-05 | Prototype | Inspect indexed documents with known dates and check the dates in a conflicting-source result. | Draft — tested sources assumed dated |
| SR-DATA-012 | Keep shared team-path and Project content and steps across employees and sign-ins; store active step progress separately per employee, delete that progress at completion, and retain an employee-to-path completion record. Keep enough path-to-source provenance to give affected completers a general warning after a relevant source change. | UC-11, UC-12; SOW milestones 2 and 7 | Prototype | Have two employees use one path, complete it for one, inspect retained shared content and completion record, then change an associated source and inspect the warning. | Draft — reconciled with team decision |
| SR-DATA-013 | Use relevant common-pool documentation for each admin-supplied team-path keyword; a source document may support paths for different teams. | UC-06; SR-FUNC-028; SOW milestone 2 | Prototype | Compare Software Database and API paths and reuse a relevant source in another team's path. | Draft — reconciled with common-pool decision |
| SR-DATA-014 | Do not retain company-chatbot questions or answers in OnboardAI's data store. | UC-05; SOW milestone 6 | First chatbot iteration | Use the chatbot, then inspect OnboardAI's stored data for the question and answer. | Draft |

## Data inventory

| Data category | Source / owner | Sensitivity | Retention or deletion need | Scope |
| --- | --- | --- | --- | --- |
| Approved real documentation | Public GitHub Markdown repository or website/wiki; owner to identify | To classify before use | To define | Prototype evaluation |
| Realistic sample documentation | Created by the project team | To define | To define | Prototype evaluation |
| Shared team path or Project and employee step-progress state | Admin generation and employee activity | To classify | Keep shared definitions and steps after any one employee completes; keep per-employee step progress across sign-ins while active and delete that progress at completion | Prototype |
| Completion record | Employee and completed path | To classify | Keep the employee-to-completed-path record; exact fields and retention period to define in design | Prototype |
| Company-chatbot questions and answers | Company chatbot | To classify | Do not retain in OnboardAI | First chatbot iteration |

**Completion-change caution:** Retain the shared path or Project and its source provenance, plus a completion record linking the employee to it. Delete that employee's step-progress state at completion. If associated source material later changes, show a general path-changed warning; no completed-step history is needed.

**Prototype corpus assumption:** Each tested path keyword has at least some relevant documentation in the common pool. Sources used to demonstrate conflicting information provide a creation or last-updated timestamp. A generation request with no relevant source material at all is outside the agreed evaluation scenario; behavior for that case remains undecided.
