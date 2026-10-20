# Knowledge, retrieval, and AI design

## Questions

- How does approved content enter, update, and leave the system?
- How are provenance, versions, source location, and permissions preserved through transformations?
- How is eligible material searched, filtered, ranked, and passed to an answer generator?
- How are answers grounded and cited, and when does the system abstain?
- How are stale, conflicting, malformed, or malicious sources handled?
- What data is sent to external AI services, if any?

## Source and answer flows

| Step | Input | Processing and policy | Output | Failure or uncertainty behavior | Requirement / rule |
| --- | --- | --- | --- | --- | --- |
| Team-path generation search | Signed-in admin of the destination team, keyword | Search the common indexed pool for evidence relevant to the requested path; preserve original-source links. Path ownership does not make a source exclusive to that team. | Evidence for a reusable team-path draft | Show insufficient evidence or generation failure without publishing an incomplete path | AR-LEARN-001, AR-LEARN-006 |
| Project generation search | Signed-in admin, keyword | Search the full indexed document pool for material relevant to the keyword. The Project and its sources are not assigned to a team. | Evidence for a reusable Project draft, with source references | Show insufficient evidence or generation failure without saving an incomplete Project | AR-LEARN-008; AR-ACCESS-009 |
| Company-chatbot MCP search | Signed-in employee or admin with verified per-user token, knowledge request | Apply the first-iteration chatbot policy: search all scraped documents regardless of team | Source-backed knowledge and citations | Deny invalid identity; return unavailable result on retrieval failure | AR-ACCESS-004; AR-OPS-004 |

## Chosen approach and rationale

**Team design:** PostgreSQL with pgvector is the selected vector storage and similarity-search technology. An admin gives the path generator a topic or keyword; it saves reusable team-owned path content and ordered steps at runtime using relevant common-pool documents. An admin reviews a new path before first publication. When changed source material affects a published path, successfully regenerated changes publish automatically without another admin review; a failed refresh leaves the current path available with a freshness warning. Previously completed changed steps require a revisit notice, while future steps update quietly. The embedding model, chunking method, keyword or hybrid search, ranking, and citation construction remain open. Employee path visibility and chatbot retrieval use their distinct authorization rules.

**Project generation scope:** A Project is generated from an admin's keyword against the indexed documentation pool. Generation searches the full pool without a team filter. A Project is not owned by a team. The team assumes indexed documents are not confidential and allows team admins to inspect sources during Project creation and review. A Project assignment governs which employees see the Project and can follow its linked original sources. The exact retrieval/ranking method and generator component boundary remain open.

**Project assignment review and refresh:** The admin assigning a Project reviews its shared content for that employee before the assignment becomes visible. Each assigning admin reviews the Project, even if another admin reviewed it for a different employee. A successful source-driven regeneration becomes available to existing assignees automatically without another review. Active employees receive the agreed step-change behavior; completers receive only a general warning when source material associated with their finished Project changes. The shared Project and steps remain available after any one employee completes them.

**Original-source links:** Employees must be able to open every original document linked from a team path or Project assigned to them. The searchable index can hold derived text and source references without becoming an employee-facing library of full document copies. Opening an original link depends on the source system's own access rules; the prototype's first GitHub source is public. The later website or wiki connector must provide original links that assigned employees can open; choose its sign-in mechanism when selecting the source. Path ownership does not make a supporting document exclusive to that team.

**Serious alternatives and tradeoffs:**

**Source and answer sequence diagrams:**

**Verification / open questions:**
