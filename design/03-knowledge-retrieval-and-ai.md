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

## Chosen approach and rationale

**Team design:** PostgreSQL with pgvector is the selected vector storage and similarity-search technology. An admin gives the path generator a topic or keyword; it saves reusable team-owned path content and ordered steps at runtime. An admin reviews a new path before first publication. When changed source material affects a published path, successfully regenerated changes publish automatically without another admin review; a failed refresh leaves the current path available with a freshness warning. Previously completed changed steps require a revisit notice, while future steps update quietly. The embedding model, chunking method, keyword or hybrid search, ranking, and citation construction remain open. Retrieval must apply the appropriate employee-interface or MCP access policy before returning source-backed material.

**Serious alternatives and tradeoffs:**

**Source and answer sequence diagrams:**

**Verification / open questions:**
