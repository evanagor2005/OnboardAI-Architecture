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
| AR-DATA-001 | Preserve each ingested item's source reference, team or shared classification, and creation or last-updated timestamp with the retrievable content derived from it. | SR-DATA-001, SR-DATA-003, SR-DATA-005, SR-DATA-011 | Source records, index, citations | Trace retrieved examples from two teams and shared content to their source, classification, and timestamp. | Draft — derived |
| AR-DATA-002 | Propagate additions, changes, and removals of GitHub Markdown files into retrievable knowledge on the milestone-2 ten-minute polling cycle; support the agreed refresh behavior for the later website or wiki source. | SR-DATA-002, SR-DATA-004, SR-DATA-010 | Source connectors, index refresh | Add, change, and remove source items and inspect retrieval after the applicable refresh. | Draft — derived |
| AR-DATA-003 | Keep the authoritative source identity and version distinguishable from indexed, generated, and other rebuildable data. | SR-DATA-003, SR-DATA-004, SR-FUNC-025 | Source records, index, generated paths | Trace a changed document to refreshed retrieval and affected path content without losing the source reference. | Draft — derived |
| AR-DATA-004 | Persist each active path and its completed-step state separately for each employee and topic across sign-ins. | SR-FUNC-023, SR-FUNC-024, SR-FUNC-030, SR-DATA-012 | Active path and progress storage | Resume two topic paths after sign-in and verify independent progress. | Draft — derived |
| AR-DATA-005 | Delete a finished path's generated content, step details, and displayed completion record after completion, as required for both onboarding and assigned learning. | SR-FUNC-027, SR-DATA-012 | Path and progress storage | Complete both path types and inspect stored state after the completion record has been shown. | Draft — derived; post-completion caution dependency open |
| AR-DATA-006 | Support identification of an employee affected when source material from a finished path later changes, without retaining the deleted items named in AR-DATA-005. | SR-FUNC-032, SR-DATA-012, SR-INT-012 | Source-change tracking and completion lifecycle | Finish a path, verify required deletion, change associated source material, and inspect the caution. | Draft — unresolved: team must approve what association, if any, may remain |
| AR-DATA-007 | Avoid storing company-chatbot questions or answers in OnboardAI's data store. | SR-DATA-014, SR-SEC-015 | MCP boundary, data stores, logs | Use the chatbot and inspect OnboardAI's persisted data. | Draft — derived |

## Unresolved rule dependency

AR-DATA-005 and AR-DATA-006 reflect two requirements the team gave us. The team must decide what minimal post-completion association, if any, can remain before AR-DATA-006 can be accepted or designed. No retained completion record, generated path, or step detail is implied by this draft.
