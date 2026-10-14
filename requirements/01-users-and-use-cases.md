# Users and use cases

This page records **who interacts with OnboardAI and what they are trying to accomplish**. The IDs link actors and use cases to the requirements that follow.

## Actors

An **actor** is a person, group, or external system that interacts with OnboardAI. It describes a role in an interaction, not a specific named individual or a software component inside OnboardAI.

Who uses, administers, supplies information to, or evaluates the prototype? Which actors are included now?

- **Actor ID:** Optional short label, such as `EMP`, used to link this actor to use cases.
- **Actor:** Who or what interacts with OnboardAI.
- **Goal:** What that actor wants to accomplish overall.
- **Prototype / future:** Whether the team includes this actor now, later, or not at all.
- **Notes:** Important context, boundaries, or unresolved questions.

**Team's actors:**

| Actor ID | Actor | Goal | Prototype / future | Notes |
| --- | --- | --- | --- | --- |
| EMP | Employee associated with a team | Request and follow onboarding for the employee's team; learn an assigned topic | Prototype | The employee's team determines which team knowledge is available. |
| ADM | Admin | Create a team and assign one employee a specific topic to learn | Prototype | Admins can also use the company chatbot. |
| CHAT | Company chatbot | Request permitted, source-backed knowledge from OnboardAI through the MCP | Prototype | All signed-in employees and admins may use it; company integration is a dependency. |
| DOC | Documentation source | Supply team knowledge for onboarding and individual topics | Prototype | The prototype starts with one source and later adds a different type of source. |

## Use cases

Each **use case** is one task an actor tries to complete. The **trigger** is the event or need that starts the task. It is different from the action the actor takes. Describe a successful result and the response when the task cannot be completed.

- **Use case ID:** Optional short label, such as `UC-01`, for linking to requirements and tests.
- **Actor:** Which actor from the table above performs the task.
- **Trigger:** What makes the actor need to act *now*.
- **Task:** What the actor tries to do with OnboardAI.
- **Successful result:** What the actor can observe when the task works.
- **If it cannot work:** What the actor sees or can do when information, access, or a dependency is missing.
- **In prototype?:** Yes, no, or undecided. This is a scope decision, not a technology choice.

**Team's use cases:**

| Use case ID | Actor | Trigger (why now?) | Task | Successful result | If it cannot work | In prototype? |
| --- | --- | --- | --- | --- | --- | --- |
| UC-01 | Admin | A team needs to be represented in OnboardAI | Create a team | The team is available for team-based onboarding | The admin sees that creation did not succeed | Yes — milestone 1 |
| UC-02 | Employee associated with a team | The employee is starting onboarding | Request a team onboarding path | A path is created on request from knowledge relevant to that team, with source references | The employee sees that a path could not be created from available, permitted knowledge | Yes — milestones 2 and 4 |
| UC-03 | Admin | One employee needs to learn a specific documented topic | Assign that topic to the employee | The assignment is associated with the intended employee | The admin sees that the assignment did not succeed | Yes — milestone 7 |
| UC-04 | Employee with an assigned topic | The employee is ready to learn the assigned topic | Open the individual learning path | The employee sees a path tied to relevant hub documents | The employee sees that the path is unavailable or lacks permitted source material | Yes — milestone 7 |
| UC-05 | Signed-in employee or admin | The person asks the chatbot an onboarding question | Request OnboardAI knowledge through the chatbot | The chatbot receives knowledge and sources permitted for that person | The chatbot receives no restricted content and communicates when access or knowledge is unavailable | Yes — milestone 6 |

## Journey questions

Use these prompts after identifying the actors and use cases. They help expose missing steps and exceptions; they are not extra columns to fill for every row.

- What must a user understand before starting?
- What can they inspect or correct during the task?
- When does a person take over from the system?
- Which journeys must be demonstrated for acceptance?

**Team answers:**
