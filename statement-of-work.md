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
| DEL-001 | Team-based onboarding | To define |
| DEL-002 | MCP registered with the company chatbot | To define |
| DEL-003 | Individual-based learning on a specific topic in the documentation hub | One employee can access a learning path for a specific topic drawn from the hub's documents. |

The team will define the remaining completion evidence for each deliverable. Individual-based learning means enabling one person to learn a specific topic contained in the documentation hub; it does not require an adaptive learning system.

## Constraints and dependencies

What time, budget, team, data, privacy, hosting, course, or stakeholder constraints govern the work? What must another party provide?

**Team answer:**

**Dependency to confirm:** The company chatbot must allow the team to register the MCP and provide a way to enforce the appropriate employee access rules.

## Development phases and milestones

Each milestone is a phase of development. The exit condition describes what the team should be able to demonstrate before moving to the next phase.

| Milestone | Exit condition |
| --- | --- |
| 1. End-to-end skeleton | An admin signs in and creates a team. An employee signs in, selects one team without admin assignment, and sees basic onboarding information and a basic team-based path. The selection establishes the employee's team for this early prototype: that team's and company-wide shared documents can be used, while other teams' documents are excluded. The initial MCP processes one source containing team-specific and shared information and builds the initial vector database. The team records how it will compare onboarding speed, retention, and application during evaluation and confirms the company chatbot integration requirements. |
| 2. Dynamic software engineer onboarding | A software engineer employee requests a path, and the prototype creates and displays one from connected knowledge rather than a prewritten path. The team verifies that the path uses software-relevant material, excludes unauthorized material, and identifies the source of each learning item. |
| 3. More data and multiple teams | The MCP and supporting knowledge pipeline process a team-defined, larger collection covering at least two teams. Retrieval checks show that each request returns relevant material for the authorized team and withholds restricted material from other teams. The team records the observed results and failures to guide tuning. |
| 4. Multiple dynamic team paths | Employees from at least two teams request paths and receive distinct paths generated from their respective teams' knowledge. The team verifies the content and source references in both paths and checks that neither path exposes restricted content from the other team. |
| 5. Documentation-agnostic ingestion | The team connects a second, different type of documentation source through the common ingestion process and generates paths using content from both sources. A changed or removed document is reflected in the retrievable knowledge and its source references after the agreed refresh process. |
| 6. Finalized UI/UX and company chatbot | Users can complete the agreed employee and admin journeys through the finished interface. Employee team association comes from role information linked to their authenticated identity instead of employee selection. The MCP is registered with the company chatbot; signed-in employees and admins can request relevant, source-backed knowledge there. The team verifies that chatbot responses obey each person's access rules, including a denied-access case. |
| 7. Individually assigned paths | An admin assigns one employee a specific topic contained in the documentation hub. That employee can access a path for the topic, with learning items tied to the relevant documents. The team verifies that the assignment is associated with the intended employee and cannot be made by an employee. |
| 8. Deployment | The integrated prototype runs in the chosen evaluation environment. The team repeats the core employee, admin, and chatbot journeys there, checks access controls, and confirms the system can be restarted without losing required data. |
| 9. Human prototype testing | Representative people complete team onboarding and individual-topic learning tasks in the deployed prototype. The team records task times, a knowledge check, a later retention check, an application task, and usability feedback, then reports the results and limitations against its evaluation plan. |
| 10. Iterate on feedback | The team ranks findings from human testing, selects improvements, implements them, and repeats the affected checks. The final demonstration shows the changes made, the results, and any remaining limitations. |

Milestone 2 focuses on the software engineer role. Individually assigned paths are planned for milestone 7.

## Acceptance and handoff

What evidence confirms the deliverables are complete? What will be handed off at the end?

**Team answer:**

## Changes

How will changes to the plan be decided and their effect on the deliverables be recorded?

**Team answer:**
