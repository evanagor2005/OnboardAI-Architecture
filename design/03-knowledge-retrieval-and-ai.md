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
| Ordinary employee onboarding search | Signed-in employee, team path or onboarding request | Search documents classified for the employee's invited team plus company-wide shared documents; exclude other teams' documents | Permitted evidence with source references | Deny missing identity; show an unavailable result if retrieval fails | AR-ACCESS-002; AR-SYS-002 |
| Project generation search | Signed-in admin, keyword, optional team filter | With no filter, search all indexed documents. With a filter, search that team's documents plus company-wide shared documents. The filter selects source material and does not assign the Project to a team. | Evidence for a reusable Project draft, with source references | Show insufficient evidence or generation failure without publishing an incomplete Project | AR-LEARN-008; AR-ACCESS-009 |
| Company-chatbot MCP search | Signed-in employee or admin with verified per-user token, knowledge request | Apply the first-iteration chatbot policy: search all scraped documents regardless of team | Source-backed knowledge and citations | Deny invalid identity; return unavailable result on retrieval failure | AR-ACCESS-004; AR-OPS-004 |

## Chosen approach and rationale

**Team design:** PostgreSQL with pgvector is the selected vector storage and similarity-search technology. An admin gives the path generator a topic or keyword; it saves reusable team-owned path content and ordered steps at runtime. An admin reviews a new path before first publication. When changed source material affects a published path, successfully regenerated changes publish automatically without another admin review; a failed refresh leaves the current path available with a freshness warning. Previously completed changed steps require a revisit notice, while future steps update quietly. The embedding model, chunking method, keyword or hybrid search, ranking, and citation construction remain open. Retrieval must apply the appropriate employee-interface or MCP access policy before returning source-backed material.

**Project generation scope:** A Project is generated from an admin's keyword against the indexed documentation pool. The optional team filter narrows evidence to that team's documents plus company-wide shared documents; omitting it searches the full indexed pool. A Project is not owned by the filtered team. The team assumes indexed documents are not confidential and allows team admins to inspect cross-team source documents during Project creation and review. This admin permission does not change ordinary employee onboarding access. A Project assignment governs which employees see the Project and its linked cross-team material. The exact retrieval/ranking method and generator component boundary remain open.

**Project publication and refresh:** The creating admin must review a new generated Project before first publication. After publication, a successful source-driven regeneration publishes automatically without another admin review. Active employees receive the agreed step-change behavior; completers receive only a general warning when source material associated with their finished Project changes. The shared Project and steps remain available after any one employee completes them.

**Original-source links:** Employees must be able to open every original document linked from a team path or Project assigned to them. The searchable index can hold derived text and source references without becoming an employee-facing library of full document copies. Opening an original link depends on the source system's own access rules; the prototype's first GitHub source is public. When choosing a later website or wiki source, verify that intended employees can open its linked pages, or design an authorized way to provide access. Path ownership does not make a supporting document exclusive to that team.

**Serious alternatives and tradeoffs:**

**Source and answer sequence diagrams:**

**Verification / open questions:**
