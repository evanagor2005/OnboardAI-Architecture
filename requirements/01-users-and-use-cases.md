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
| EMP | Employee associated with one team | Accept a team invitation, follow available team paths, and learn through assigned Projects | Prototype | Team association is set by the accepted invitation; the employee cannot choose or switch teams directly. |
| ADM | Team admin | Administer appointed teams, appoint additional admins to those teams, invite employees to administered teams, generate and review team paths and Projects, and assign Projects to employees on administered teams | Prototype | The superuser creates teams and may appoint their admins. One admin may administer multiple teams. Admins can also use the company chatbot. |
| SUPER | Django superuser | Hold the highest level of administration, create teams, appoint their admins, invite someone to any team, and assign Projects to employees across teams | Prototype | Other superuser actions remain to be defined. |
| CHAT | Company chatbot | Request source-backed knowledge from OnboardAI through the MCP | Prototype | In its first iteration, all signed-in employees and admins may use the chatbot to access all scraped documents. |
| DOC | Documentation source | Supply the common indexed knowledge pool used to build team paths and Projects | Prototype | A source document may support paths for multiple teams; path ownership does not confer document ownership. The prototype starts with one source and later adds a different type. |

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
| UC-01 | Django superuser | A team needs to be represented in OnboardAI | Create a team | The team is available for team-based onboarding | The superuser sees that creation did not succeed | Yes — milestone 1 |
| UC-02 | Employee associated with a team | The employee is starting onboarding | Open a published team path available to that employee | The employee follows saved steps, tracks progress, and can open each linked original source | The employee sees that no path has been assigned or that an available path is temporarily unavailable | Yes — milestones 2 and 4 |
| UC-03 | Team admin or Django superuser | Employees need a specific learning topic | Generate or select a reusable Project, review it for each eligible employee being assigned, and make each reviewed assignment visible | The Project is saved independently of employees and visible to each employee after the assigning admin reviews that assignment | The admin sees generation, review, or assignment failure and cannot assign outside their authority | Yes — milestone 7 |
| UC-04 | Employee with an assigned Project | The employee is ready to learn the assigned topic | Open the saved Project | The employee sees its steps and can open every linked original source; progress is independent of other assignees | The employee sees that the Project is unavailable or that an original source cannot be opened | Yes — milestone 7 |
| UC-05 | Signed-in employee or admin using the company chatbot | The person asks the chatbot an onboarding question | Request OnboardAI knowledge through the chatbot | In the first iteration, the chatbot receives source-backed knowledge from the scraped documents regardless of team | The chatbot communicates when the knowledge or MCP is unavailable | Yes — milestone 6 |
| UC-06 | Admin of a team | The team needs an onboarding topic | Submit a keyword, review the generated team path and its sources, choose all-member or selected-member audience, and publish it | A reusable path belongs to the team; its assigned members can see it and open linked original sources | An incomplete or unapproved path is not shown to employees | Yes — milestones 2 and 4 |
| UC-07 | Django superuser or team admin | A person needs to join a team | Invite the person by email to join that team; a team admin chooses only a team they administer | The person receives an invitation email naming the team | The inviter sees that the invitation could not be sent or that they cannot invite to the chosen team | Yes — milestone 1 |
| UC-08 | Invitation recipient | The person receives a team invitation email | Accept the one-use, time-limited invitation and choose a username and password | An account is created and associated with the invited team | The person sees that an expired or already used invitation cannot be accepted, or that the account cannot be created | Yes — milestone 1 |
| UC-09 | Employee transferring teams | The employee needs to move to a different team | Accept an invitation initiated by the destination team's admin or the superuser | The employee's team association changes to the destination team | The employee remains on the existing team if the transfer cannot be completed | Yes — development phase open |
| UC-10 | Django superuser or appointed team admin | A team needs an admin | Appoint an admin for the team; a team admin may do so only for a team they administer | The appointed person has admin authority for that team | The authorized actor sees that the appointment did not succeed | Yes — milestone 1 |
| UC-11 | Employee with an active onboarding or assigned learning path | The employee is working through a path and a relevant document changes | Continue the path | The path reflects the changed knowledge; if a completed step changed, the employee is told to revisit it | The current path remains visible with a freshness warning if refresh fails | Yes — milestones 2 and 7 |
| UC-12 | Employee with an active team path or Project | The employee finishes the path | Complete it | The shared path or Project and steps remain; that employee's step progress is deleted and a completion record is kept. A later associated source change produces a general warning. | The employee sees that completion could not be confirmed | Yes — milestones 2 and 7 |

## Journey questions

Use these prompts after identifying the actors and use cases. They help expose missing steps and exceptions; they are not extra columns to fill for every row.

- What must a user understand before starting?
- What can they inspect or correct during the task?
- When does a person take over from the system?
- Which journeys must be demonstrated for acceptance?

**Team answers:**
