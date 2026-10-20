# Statement of work

**Status:** Draft — team approval pending  

## Product outcome measures

We will evaluate the prototype's user experience and quality by whether it helps people:

1. Complete onboarding faster.
2. Retain the knowledge they learn during onboarding.
3. Apply that knowledge to role-relevant tasks.

The team will define the baseline, measurement method, and success threshold for each outcome in the [evaluation design](design/09-evaluation-plan.md).

## Deliverables

The team plans to complete all three deliverables through the development phases below.

| Deliverable ID | Deliverable | Reviewable evidence |
| --- | --- | --- |
| DEL-001 | Team-based onboarding | Admins create and publish reusable paths for their teams from documentation; assigned employees follow source-backed paths with independent progress and relevant update notices. |
| DEL-002 | MCP registered with the company chatbot | Signed-in employees and admins can retrieve source-backed knowledge through the registered MCP from the scraped documents. |
| DEL-003 | Individual-based learning on a specific topic in the documentation hub | An admin can create a reusable, team-independent Project from a keyword and assign it to employees, each with independent progress. |

Individual-based learning means enabling one person to learn a specific topic contained in the documentation hub; it does not require an adaptive learning system.

## Constraints and dependencies

What time, budget, team, data, privacy, hosting, course, or stakeholder constraints govern the work? What must another party provide?

**Team answer:** The prototype will use a mix of real documents approved by the project team and realistic sample documents. Its tested topics are assumed to have at least some relevant documentation in the common source pool. Generating a path with no relevant source material at all is outside the agreed prototype scenario. Sources used for the conflicting-document demonstration are assumed to provide creation or update timestamps. The first documentation source is a public GitHub repository containing Markdown files. Access requirements for the second website or wiki will be chosen when that source is selected. A team path's ownership determines its employee audience; it does not make supporting documents exclusive to that team.

**Dependency to confirm:** The company chatbot must allow the team to register the MCP. In the first iteration, all signed-in employees and admins may use it. The team still needs to define how access policies could be configured in a later iteration.

OnboardAI will not retain company-chatbot questions or answers in its own data store. Any retention by the external company chatbot is outside the prototype's control and must be checked when that chatbot is selected.

## Development phases and milestones

Each milestone is a phase of development. The exit condition describes what the team should be able to demonstrate before moving to the next phase.

| Milestone | Exit condition |
| --- | --- |
| 1. End-to-end skeleton | A Django superuser is the highest administrator. An admin creates a team, and the superuser appoints its team admin. The superuser may invite someone to any team, while a team admin may invite someone only to a team they administer. One-use, time-limited invitations are sent through Mailgun. The recipient accepts, chooses a username and password, and receives an account associated with the invited team; the employee signs in and sees basic onboarding information and a basic saved team path. Keyword-based path generation and admin review are not required for this milestone. The initial MCP ingests Markdown files once from one public GitHub documentation repository and builds the initial vector index; automatic polling is not part of this milestone. The team records how it will compare onboarding speed, retention, and application during evaluation and confirms the company chatbot integration requirements. |
| 2. Dynamic software engineer onboarding | A Software team admin supplies two distinct keywords, such as Databases and APIs. OnboardAI generates and saves two reusable Software team paths from relevant documents in the common pool; the admin reviews each before publication. Assigned Software employees see the published paths, can open every linked original source, and keep independent progress across sign-ins. The team verifies source-backed steps, labeled AI-inferred steps, and labeled AI-suggested alternatives. GitHub Markdown is polled every 10 minutes. A successful source-driven path revision publishes without another admin review; an active employee revisits a changed completed step while a future step updates quietly. Failed refresh leaves the path available with a freshness warning. Completing one employee's path deletes that employee's step progress but retains the shared path and steps plus an employee-to-path completion record. A later relevant source change produces a general warning for affected completers. |
| 3. More data and multiple teams | The MCP and supporting knowledge pipeline process a team-defined, larger collection useful for at least two teams. Retrieval checks measure relevance and source attribution in the common pool. Employee-interface checks verify that employees see only team paths available to them, while the first chatbot policy is tested separately. The team records observed results and failures to guide tuning. |
| 4. Multiple dynamic team paths | Admins generate, review, and publish multiple paths for at least two teams from relevant documents in the common pool. Team membership and each path's all-member or selected-member audience determine which employees see the path. The team verifies that an unassigned employee cannot see a selected-member path, that two employees can progress independently through one shared path, and that every linked original source opens for an assigned employee. Documents may support paths for more than one team without becoming owned by either team. |
| 5. Documentation-agnostic ingestion | The team connects a website or wiki as a second documentation source through the common ingestion process and generates paths using content from both the GitHub repository and the website or wiki. A changed or removed document is reflected in the retrievable knowledge and its source references after the agreed refresh process. |
| 6. Finalized UI/UX and company chatbot | Users can complete the agreed employee and admin journeys through the finished interface. The MCP is registered with the company chatbot; in its first iteration, all signed-in employees and admins can request source-backed knowledge from all scraped documents. The team verifies chatbot authentication and the employee interface's path-visibility rules separately. |
| 7. Individually assigned Projects | A team admin generates a reusable, team-independent Project from a keyword and the common document pool, optionally narrowing its search by team context while including company-wide material. The admin reviews it before first publication. A team admin may assign the published Project to employees on teams they administer, and the Django superuser may assign it to employees on any team. One Project can serve multiple employees, and one employee can work on multiple Projects, each with separate progress. Employees can open every linked original source in their assigned Projects. Source-driven revisions, active progress, completion, and general later-change warnings follow the same lifecycle as team paths. The team verifies that employees cannot assign Projects and team admins cannot assign employees outside their administered teams. |
| 8. Deployment | The integrated prototype runs in the chosen evaluation environment. The team repeats the core employee, admin, and chatbot journeys there, checks access controls, and confirms the system can be restarted without losing required data. |
| 9. Human prototype testing | Representative people complete team onboarding and individual-topic learning tasks in the deployed prototype using a mix of approved real and realistic sample documents. The team records task times, a knowledge check, a later retention check, an application task, and usability feedback, then reports the results and limitations against its evaluation plan. |
| 10. Iterate on feedback | The team ranks findings from human testing, selects improvements, implements them, and repeats the affected checks. The final demonstration shows the changes made, the results, and any remaining limitations. |

Milestone 2 focuses on the software engineer role. Individually assigned paths are planned for milestone 7. Whether the UI/UX phase also integrates an external identity provider remains open now that milestone 1 creates invite-based accounts.

Team admins choose path keywords and review generated team paths before employees see them. Published team paths and Projects are reusable and survive an employee's completion. Completion deletes only that employee's step-progress state, keeps a record linking the employee to the completed path or Project, and supports a general warning if associated source material later changes.

## Acceptance and handoff

What evidence confirms the deliverables are complete? What will be handed off at the end?

**Team answer:**

## Changes

How will changes to the plan be decided and their effect on the deliverables be recorded?

**Team answer:**
