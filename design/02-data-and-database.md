# Data model and database design

Start from [data and knowledge rules](../adr/02-data-and-knowledge.md), especially access patterns and consistency needs. Record product comparisons in [technology choices](08-technology-choices.md).

## Questions

- What entities and relationships exist in the agreed prototype scope?
- Which data is authoritative, derived, cached, or disposable?
- Which stores serve records, document content, indexes, and temporary data?
- What tables or collections, keys, indexes, and constraints implement the access patterns?
- How are source versions, citations, permissions, migrations, deletion, and backup represented?
- Can a document be associated with multiple teams, or with exactly one team or the company-wide shared category?

## Domain model

| Entity | Meaning and owner | Identifier | Relationships | Lifecycle | Requirement / rule |
| --- | --- | --- | --- | --- | --- |

## Physical design

| Entity or derived data | Store | Table / collection | Keys / indexes | Integrity or consistency rule | Access pattern |
| --- | --- | --- | --- | --- | --- |

## Chosen approach and rationale

**Team design:** The team selected PostgreSQL with pgvector for the prototype's application records and vector search. This selects the DBMS and vector technology, not the final tables, indexes, or deployment layout. Team access classification applies to the whole document. Indexed sections or chunks derived from that document inherit its classification; different sections of one document will not be assigned different team access. Existing requirements also include company-wide shared documents. Whether one document may be associated with multiple teams remains open.

**Serious alternatives and tradeoffs:** The team compared PostgreSQL with pgvector against PostgreSQL plus Qdrant. The chosen approach has fewer data systems to operate and synchronize. A separate vector service remains a possible change if representative filtered retrieval tests show a concrete need.

**Migration, backup, and deletion plan:**

**Editable schema diagram:**

**Verification / open questions:** Verify that all retrieved chunks from a team document carry the document's team classification and that employee-interface searches exclude other teams' documents. Decide whether a document may be associated with multiple teams or must be either associated with one team or company-wide shared. Define entities, relationships, tables, indexes, version handling, and deletion behavior.
