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
