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
| EMP | Employee associated with one team | Accept a team invitation, request and follow that team's onboarding, and learn an assigned topic | Prototype | Team association is set by the accepted invitation; the employee cannot choose or switch teams directly. |
| ADM | Team admin | Create or administer a team, invite an employee to the admin's team, and assign one employee a specific topic to learn | Prototype | Admins can also use the company chatbot. Whether a team creator automatically becomes its admin is open. |
| SUPER | Django superuser | Hold the highest level of administration and invite someone to any team | Prototype | How team admins are first designated, and any other superuser actions, remain to be defined. |
| CHAT | Company chatbot | Request source-backed knowledge from OnboardAI through the MCP | Prototype | In its first iteration, all signed-in employees and admins may use the chatbot to access all scraped documents. |
| DOC | Documentation source | Supply team and company-wide shared knowledge for onboarding and individual topics | Prototype | The prototype starts with one source and later adds a different type of source. |

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
| UC-02 | Employee associated with a team | The employee is starting onboarding | Request a team onboarding path | A path is created on request from knowledge relevant to that team, with ordered steps, summaries, and source links | The employee sees that a path could not be created from available, permitted knowledge | Yes — milestones 2 and 4 |
| UC-03 | Admin | One employee needs to learn a specific documented topic | Assign that topic to the employee | The assignment is associated with the intended employee | The admin sees that the assignment did not succeed | Yes — milestone 7 |
| UC-04 | Employee with an assigned topic | The employee is ready to learn the assigned topic | Open the individual learning path | The employee sees a path tied to relevant hub documents | The employee sees that the path is unavailable or lacks permitted source material | Yes — milestone 7 |
| UC-05 | Signed-in employee or admin using the company chatbot | The person asks the chatbot an onboarding question | Request OnboardAI knowledge through the chatbot | In the first iteration, the chatbot receives source-backed knowledge from the scraped documents regardless of team | The chatbot communicates when the knowledge or MCP is unavailable | Yes — milestone 6 |
| UC-07 | Django superuser or team admin | A person needs to join a team | Invite the person by email to join that team; a team admin chooses only a team they administer | The person receives an invitation email naming the team | The inviter sees that the invitation could not be sent or that they cannot invite to the chosen team | Yes — milestone 1 |
| UC-08 | Invitation recipient | The person receives a team invitation email | Accept the invitation and choose a username and password | An account is created and associated with the invited team | The person sees that the invitation cannot be accepted or the account cannot be created | Yes — milestone 1 |
| UC-09 | Employee transferring teams | The employee needs to move to a different team | Accept an invitation initiated by an admin of the destination team | The employee's team association changes to the destination team | The employee remains on the existing team if the transfer cannot be completed | Yes — development phase open |

## Journey questions

Use these prompts after identifying the actors and use cases. They help expose missing steps and exceptions; they are not extra columns to fill for every row.

- What must a user understand before starting?
- What can they inspect or correct during the task?
- When does a person take over from the system?
- Which journeys must be demonstrated for acceptance?

**Team answers:**
