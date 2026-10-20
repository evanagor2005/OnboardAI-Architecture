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

**Confirmed relationships, before choosing tables:** One team may own many paths; each path belongs to one team and is independent of any employee. An invited employee is associated with one team. A team can have multiple appointed team admins, and one person can administer multiple teams; administration is a many-to-many relationship separate from employee team membership. A path may be assigned to every member of its team or only to designated members; other members do not see that path. Every visible path is assigned for completion. The prototype does not have a separate required/optional setting. Each participating employee has their own progress and completion record against the shared team path. Completing a path must not delete the team-owned path. Path assignment does not restrict access to the underlying team documents; document access follows the document's team or shared classification.

**Confirmed path lifecycle:** An admin supplies a topic or keyword; the path generator creates and saves reusable path content and ordered steps at runtime. The admin reviews a new path before its first publication. When a source document changes in a way that affects a published path, a successfully regenerated revision goes live without another admin review. Existing active-path behavior still applies: a changed completed step prompts a revisit, while a changed future step updates without a notice. If refresh fails, keep the current path and show a freshness warning. Read-and-continue and question steps are in scope; question grading and answer storage still need design.

| Entity | Meaning and owner | Identifier | Relationships | Lifecycle | Requirement / rule |
| --- | --- | --- | --- | --- | --- |
| Team | Named group that owns paths and receives invited employees | Team ID | One team has many paths and may have multiple appointed admins | Created by an authorized admin; later editing/archiving open | SR-FUNC-002, SR-FUNC-010, SR-FUNC-017; team decision |
| Team-admin appointment | One user's authority to administer one team | Team ID plus user ID, exact key form open | Many-to-many: one team may have multiple admins, and one user may administer multiple teams | Appointed by the Django superuser; removal behavior open | SR-FUNC-017, SR-SEC-010; team decision |
| Team path | Reusable onboarding path owned by one team | Path ID, exact key name open | One team has many paths; one path may be assigned to all or selected team members | Persists independently of each employee's progress and completion | Team decision; requirements revision pending |
| Selected-member path assignment | One employee's eligibility to see and complete one selected-members path | Path ID plus employee ID, exact key form open | Joins a team path to one employee on the same team; one row per path–employee pair | Added or removed as the path's selected audience changes | Team decision; requirements revision pending |

## Physical design

**Confirmed relational choice:** No cell in `team_paths` holds a set of users. An all-team path uses team membership; a selected-members path uses a separate join table with one row per path–employee pair. The same path content is reused while employee progress is stored separately. The table names and remaining columns below are still proposals.

| Entity or derived data | Store | Table / collection | Keys / indexes | Integrity or consistency rule | Access pattern |
| --- | --- | --- | --- | --- | --- |
| Team | PostgreSQL | `teams` | Team ID primary key; name; optional description; creation timestamp proposed | Team identity persists across name changes; whether names must be unique remains open | Create and list teams; join to paths and invited employees |
| Team admins | PostgreSQL | Separate appointment table chosen; `team_admins` is a proposed name | One row per team ID and user ID; unique pair proposed | Many-to-many admin relationship; appointments require superuser authority | Check which teams an admin may administer and invite into |
| Team-owned path | PostgreSQL | `team_paths` (proposed) | Path ID; team ID; topic/keyword; audience mode; current published version reference | One path belongs to one team; all-team or selected-members audience; path persists when an employee completes it | List paths assigned to a team member |
| Selected path audience | PostgreSQL | Separate join table chosen; `team_path_assignments` is a proposed name | One row per path ID and employee ID; unique pair | Used for selected-members paths; employee must belong to the path's team | Check whether a team member can see the path |
| Generated path revision | PostgreSQL | `team_path_versions` (proposed) | Version ID; path ID; version number; publication state/time | Initial version awaits admin review; later source-driven revisions publish automatically after successful regeneration | Read current version; compare changed steps |
| Ordered path step and content | PostgreSQL | `team_path_steps` (proposed) | Step ID; version ID; order; step type; saved teaching content and question data as applicable | Steps belong to one version; unique order within a version; source references still to model | Show the next read or question step |
| Employee progress and completion | PostgreSQL | Tables to design | Employee ID and path ID, with step identity where needed | Progress is per employee; completion does not delete the shared team path | Resume, complete, and revisit affected steps |

The displayed step count can be derived from the published version's step rows. Storing a separate count on `team_paths` is an optional performance choice that would require keeping it synchronized. A stable way to match the same logical step across versions is still needed for revisit notices.

## Chosen approach and rationale

**Team design:** The team selected PostgreSQL with pgvector for the prototype's application records and vector search. This selects the DBMS and vector technology, not the final tables, indexes, or deployment layout. Team access classification applies to the whole document. Indexed sections or chunks derived from that document inherit its classification; different sections of one document will not be assigned different team access. Existing requirements also include company-wide shared documents. Whether one document may be associated with multiple teams remains open.

**Serious alternatives and tradeoffs:** The team compared PostgreSQL with pgvector against PostgreSQL plus Qdrant. The chosen approach has fewer data systems to operate and synchronize. A separate vector service remains a possible change if representative filtered retrieval tests show a concrete need.

**Migration, backup, and deletion plan:**

**Editable schema diagram:**

**Verification / open questions:** Verify that all retrieved chunks from a team document carry the document's team classification and that employee-interface searches exclude other teams' documents. Verify that unassigned team members do not see a designated-members path, while their access to team documents remains unchanged. Decide whether a team admin must also be an employee member of every team they administer, and whether administering another team grants access to that team's employee paths or documents. Decide whether a document may be associated with multiple teams or must be either associated with one team or company-wide shared. Resolve question grading, step-source links, stable step identity across versions, employee progress retention, and exact keys/indexes. Reconcile the older employee-requested path and path-deletion requirements with this shared team-path model.
