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

**Team answer:** The prototype will use a mix of real documents approved by the project team and realistic sample documents. Its tested roles and topics are assumed to have at least some relevant documentation, which may consist only of company-wide shared material for a team. Generating a path with no relevant source material at all is outside the agreed prototype scenario. The first documentation source is a public GitHub repository containing Markdown files. Whether the second website or wiki requires sign-in remains undecided.

**Dependency to confirm:** The company chatbot must allow the team to register the MCP. In the first iteration, all signed-in employees and admins may use it. The team still needs to define how access policies could be configured in a later iteration.

## Development phases and milestones

Each milestone is a phase of development. The exit condition describes what the team should be able to demonstrate before moving to the next phase.

| Milestone | Exit condition |
| --- | --- |
| 1. End-to-end skeleton | A Django superuser is the highest administrator. An admin creates a team, and the superuser appoints its team admin. The superuser may invite someone to any team, while a team admin may invite someone only to a team they administer. Invitations are sent through Mailgun. The recipient accepts, chooses a username and password, and receives an account associated with the invited team; the employee signs in and sees basic onboarding information and a basic team-based path. The initial MCP ingests Markdown files once from one public GitHub documentation repository containing team-specific and shared information and builds the initial vector database; automatic polling is not part of this milestone. The team records how it will compare onboarding speed, retention, and application during evaluation and confirms the company chatbot integration requirements. |
| 2. Dynamic software engineer onboarding | OnboardAI derives onboarding topics from the ingested Software documentation. A software engineer requests paths for two distinct topics, such as Databases and APIs, and the prototype creates and displays different paths from topic-relevant knowledge rather than prewritten paths. The team verifies that paths exclude unauthorized material and identify source-backed steps, AI-inferred steps, and AI-suggested alternatives distinctly. An employee may keep more than one topic path in progress. The GitHub source is polled every 10 minutes. If a source change conflicts with an active path, that path updates; the employee is told to revisit any already completed step that changed, while future steps are updated in the path. Each path is removed when finished. |
| 3. More data and multiple teams | The MCP and supporting knowledge pipeline process a team-defined, larger collection covering at least two teams. Retrieval checks show that each request returns relevant material for the authorized team and withholds restricted material from other teams. The team records the observed results and failures to guide tuning. |
| 4. Multiple dynamic team paths | Employees from at least two teams with team-specific documentation request paths and receive distinct paths generated from their respective teams' knowledge. The team verifies the content and source references in both paths and checks that neither path exposes restricted content from the other team. If a tested team has only company-wide shared documentation, its employee still receives a company-wide onboarding path and sees that no team-specific onboarding path is available. |
| 5. Documentation-agnostic ingestion | The team connects a website or wiki as a second documentation source through the common ingestion process and generates paths using content from both the GitHub repository and the website or wiki. A changed or removed document is reflected in the retrievable knowledge and its source references after the agreed refresh process. |
| 6. Finalized UI/UX and company chatbot | Users can complete the agreed employee and admin journeys through the finished interface. The MCP is registered with the company chatbot; in its first iteration, all signed-in employees and admins can request source-backed knowledge from all scraped documents regardless of team. The team verifies chatbot access and the employee interface's team-specific access separately. |
| 7. Individually assigned paths | A team admin assigns an employee on a team they administer a specific topic contained in the documentation hub; the Django superuser may assign a topic to an employee on any team. The assigned employee can access a path for the topic, with learning items tied to the relevant documents and the same visible distinction between source-backed steps, AI inferences, and AI-suggested alternatives. An explicit assignment may make documents from another team available to that employee for the assigned path; ordinary team onboarding remains limited to the employee's team and shared documents. The team verifies that employees cannot make assignments and team admins cannot assign employees outside their teams. |
| 8. Deployment | The integrated prototype runs in the chosen evaluation environment. The team repeats the core employee, admin, and chatbot journeys there, checks access controls, and confirms the system can be restarted without losing required data. |
| 9. Human prototype testing | Representative people complete team onboarding and individual-topic learning tasks in the deployed prototype using a mix of approved real and realistic sample documents. The team records task times, a knowledge check, a later retention check, an application task, and usability feedback, then reports the results and limitations against its evaluation plan. |
| 10. Iterate on feedback | The team ranks findings from human testing, selects improvements, implements them, and repeats the affected checks. The final demonstration shows the changes made, the results, and any remaining limitations. |

Milestone 2 focuses on the software engineer role. Individually assigned paths are planned for milestone 7. Whether the UI/UX phase also integrates an external identity provider remains open now that milestone 1 creates invite-based accounts.

Within one team, OnboardAI derives onboarding topics from the documentation and produces distinct paths for those topics. Milestone 2 demonstrates this with Software Database and API paths. How an employee chooses among derived topics remains to be decided.

## Acceptance and handoff

What evidence confirms the deliverables are complete? What will be handed off at the end?

**Team answer:**

## Changes

How will changes to the plan be decided and their effect on the deliverables be recorded?

**Team answer:**
