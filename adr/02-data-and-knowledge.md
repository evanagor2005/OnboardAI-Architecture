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
| AR-DATA-001 | Preserve each ingested item's source reference, team or shared classification, and creation or last-updated timestamp with the retrievable content derived from it. | SR-DATA-001, SR-DATA-003, SR-DATA-005, SR-DATA-011 | Source records, index, citations | Trace retrieved examples from two teams and shared content to their source, classification, and timestamp. | Accepted |
| AR-DATA-002 | Propagate additions, changes, and removals of GitHub Markdown files into retrievable knowledge on the milestone-2 ten-minute polling cycle; support the agreed refresh behavior for the later website or wiki source. | SR-DATA-002, SR-DATA-004, SR-DATA-010 | Source connectors, index refresh | Add, change, and remove source items and inspect retrieval after the applicable refresh. | Accepted |
| AR-DATA-003 | Keep the authoritative source identity and version distinguishable from indexed, generated, and other rebuildable data. | SR-DATA-003, SR-DATA-004, SR-FUNC-025 | Source records, index, generated paths | Trace a changed document to refreshed retrieval and affected path content without losing the source reference. | Accepted |
| AR-DATA-004 | Persist each active path and its completed-step state separately for each employee and topic across sign-ins. | SR-FUNC-023, SR-FUNC-024, SR-FUNC-030, SR-DATA-012 | Active path and progress storage | Resume two topic paths after sign-in and verify independent progress. | Accepted |
| AR-DATA-005 | Retain a completion record identifying the employee and completed path while deleting that path's generated content and step details after completion, for both onboarding and assigned learning. | SR-FUNC-027, SR-DATA-012 | Path and progress storage | Complete both path types; inspect the retained completion record and verify generated content and step details are deleted. | Accepted |
| AR-DATA-006 | Preserve the completion record's association with source documents sufficiently to identify an affected employee when material from a finished path later changes. | SR-FUNC-032, SR-DATA-012, SR-INT-012 | Source-change tracking and completion lifecycle | Finish a path, change an associated source, and verify the affected employee receives a caution. | Deferred — team will revisit whether source association is needed |
| AR-DATA-007 | Avoid storing company-chatbot questions or answers in OnboardAI's data store. | SR-DATA-014, SR-SEC-015 | MCP boundary, data stores, logs | Use the chatbot and inspect OnboardAI's persisted data. | Accepted |

## Deferred question for AR-DATA-006

The team approved keeping a record of the employee and completed path, potentially its name, while deleting generated path content and step details. The team has **not** approved storing a per-step completion history or a completion-to-source association. It will revisit what information is needed to warn an affected employee when source material from a finished path changes. The exact completion-record fields and retention period remain open.

**Question to revisit:** Can the retained user-and-path record alone identify which employees should receive a warning after a source changes? If not, what is the least additional information the team is willing to retain, or should the warning behavior change?
