# Database design

Use the [domain model](04-domain-and-data-model.md), [data rules](../adr/data-and-persistence.md), and [technology selection](13-technology-selection.md) as inputs.

## Questions

- Which stores are needed for authoritative records, document content, search data, and temporary data?
- What tables or collections, keys, relationships, constraints, and indexes implement the model?
- Which queries and writes are critical, and what consistency do they need?
- How are permissions, source versions, citations, and deletions represented without losing integrity?
- How are migrations, backup, restoration, and test data handled?

## Logical-to-physical mapping

| Domain entity | Store | Table / collection | Key | Constraints / indexes | Access pattern |
| --- | --- | --- | --- | --- | --- |

## Schema and operations

**Team design:**

**Editable schema diagram:**

**Decision-record links and open issues:**
