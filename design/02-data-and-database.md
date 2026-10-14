# Data model and database design

Start from [data and knowledge rules](../adr/02-data-and-knowledge.md), especially access patterns and consistency needs. Record product comparisons in [technology choices](08-technology-choices.md).

## Questions

- What entities and relationships exist in the agreed prototype scope?
- Which data is authoritative, derived, cached, or disposable?
- Which stores serve records, document content, indexes, and temporary data?
- What tables or collections, keys, indexes, and constraints implement the access patterns?
- How are source versions, citations, permissions, migrations, deletion, and backup represented?

## Domain model

| Entity | Meaning and owner | Identifier | Relationships | Lifecycle | Requirement / rule |
| --- | --- | --- | --- | --- | --- |

## Physical design

| Entity or derived data | Store | Table / collection | Keys / indexes | Integrity or consistency rule | Access pattern |
| --- | --- | --- | --- | --- | --- |

## Chosen approach and rationale

**Team design:**

**Serious alternatives and tradeoffs:**

**Migration, backup, and deletion plan:**

**Editable schema diagram:**

**Verification / open questions:**
