# Architecture rules — data and persistence

State what the data layer must guarantee before comparing database types or products.

## Questions

- What data shall be authoritative, derived, cached, or disposable?
- What relationships, queries, writes, and filters shall the data layer support?
- Which updates shall be atomic or immediately visible, and which may be eventually consistent?
- How shall source versions, citation locations, and permission metadata remain linked?
- What deletion, backup, restoration, and migration guarantees are required?
- What data volume, concurrency, and cost bounds shall the design support?

## Access patterns

| Operation | Actor / component | Read or write | Filters / ordering | Frequency / volume | Consistency need | Priority |
| --- | --- | --- | --- | --- | --- | --- |

## Rules

| ID | Shall statement | Source requirement(s) | Applies to | Verification method | Status |
| --- | --- | --- | --- | --- | --- |
