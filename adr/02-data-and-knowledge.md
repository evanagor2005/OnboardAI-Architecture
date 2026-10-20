# Architecture rules — data and knowledge

Use this page to define what the data layer must support **before** comparing SQL, NoSQL, search, or other products.

## Questions

- What information is authoritative, copied, generated, cached, or disposable?
- What reads, writes, filters, relationships, and volumes must be supported?
- Which changes must be atomic or immediately visible, and which may be eventually consistent?
- How shall document versions, citation locations, permissions, and provenance stay connected?
- How shall source updates, deletions, and permission changes reach derived data?
- What backup, restoration, migration, and retention guarantees are required?

## Access patterns

| Actor / operation | Read or write | Data needed | Filters / ordering | Volume / frequency | Consistency need | Priority |
| --- | --- | --- | --- | --- | --- | --- |

## Shall statements

| ID | The architecture shall... | Source requirement ID | Applies to | How verified | Status |
| --- | --- | --- | --- | --- | --- |
| AR-DATA-001 | Preserve each ingested item's source identity, original reference, and creation or last-updated timestamp with retrievable content derived from it; do not infer exclusive document ownership from a path's team. | SR-DATA-001, SR-DATA-003, SR-DATA-005, SR-DATA-011 | Source records, index, citations | Use one source in paths for two teams and trace both results to the same original reference and timestamp. | Accepted — reconciled with common-pool decision |
| AR-DATA-002 | Propagate additions, changes, and removals of GitHub Markdown files into retrievable knowledge on the milestone-2 ten-minute polling cycle; support the agreed refresh behavior for the later website or wiki source. | SR-DATA-002, SR-DATA-004, SR-DATA-010 | Source connectors, index refresh | Add, change, and remove source items and inspect retrieval after the applicable refresh. | Accepted |
| AR-DATA-003 | Keep the authoritative source identity and version distinguishable from indexed, generated, and other rebuildable data. | SR-DATA-003, SR-DATA-004, SR-FUNC-025 | Source records, index, generated paths | Trace a changed document to refreshed retrieval and affected path content without losing the source reference. | Accepted |
| AR-DATA-004 | Persist shared team-path and Project definitions separately from each employee's active completed-step state across sign-ins. | SR-FUNC-023, SR-FUNC-024, SR-FUNC-030, SR-DATA-012 | Shared paths and per-employee progress | Have two employees use one saved path, resume after sign-in, and verify their progress remains independent. | Accepted — reconciled with shared-path decision |
| AR-DATA-005 | Keep the shared team path or Project and its steps after an employee completes it; delete that employee's step-progress state and retain a completion record identifying the employee and completed path or Project. | SR-FUNC-027, SR-DATA-012; team decision | Shared path content, employee progress, completion | Have two employees use one shared path; complete it for one employee and verify shared content and the other's progress remain, the first employee's step progress is deleted, and a completion record remains. | Accepted — revised by team decision |
| AR-DATA-006 | Preserve enough association between a completed path or Project and its supporting sources to identify affected completers and show them a general warning if that source material later changes, without retaining their completed-step history. | SR-FUNC-032, SR-DATA-012, SR-INT-012; team decision | Source-change tracking and completion lifecycle | Finish a path, remove its employee step-progress state, change an associated source, and verify the affected employee receives a general path-changed warning. | Accepted — revised by team decision |
| AR-DATA-007 | Avoid storing company-chatbot questions or answers in OnboardAI's data store. | SR-DATA-014, SR-SEC-015 | MCP boundary, data stores, logs | Use the chatbot and inspect OnboardAI's persisted data. | Accepted |

## Completion and source-change decision

The shared path or Project and its steps remain available to other assignees. On completion, delete only the completing employee's step-progress state and retain a record connecting that employee to the completed path or Project. A later relevant source change needs only a general warning that the completed path has changed, not identification of the exact completed steps. The design must keep sufficient path/Project-to-source provenance to find affected completion records. Exact completion-record fields, provenance representation, and retention period remain open.
