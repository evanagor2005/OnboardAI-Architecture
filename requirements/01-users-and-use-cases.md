# Users and use cases

This page asks **who interacts with OnboardAI and what they are trying to accomplish**. Start with plain language. The IDs are short labels for linking to later requirements; add them when the team is ready.

## Actors

An **actor** is a person, group, or external system that interacts with OnboardAI. It describes a role in an interaction, not a specific named individual or a software component inside OnboardAI. Examples to consider include an employee, a knowledge owner, or an approved assistant. These examples do not mean those actors are in scope.

Who uses, administers, supplies information to, or evaluates the prototype? Which actors are included now?

- **Actor ID:** Optional short label, such as `EMP`, used to link this actor to use cases.
- **Actor:** Who or what interacts with OnboardAI.
- **Goal:** What that actor wants to accomplish overall.
- **Prototype / future:** Whether the team includes this actor now, later, or not at all.
- **Notes:** Important context, boundaries, or unresolved questions.

**Illustrative example only — not an approved actor:**

| Actor ID | Actor | Goal | Prototype / future | Notes |
| --- | --- | --- | --- | --- |
| EMP-EX | New employee | Find guidance for an unfamiliar task | Undecided | Example only |

**Team's actors:**

| Actor ID | Actor | Goal | Prototype / future | Notes |
| --- | --- | --- | --- | --- |

## Use cases

Each **use case** is one task an actor tries to complete. The **trigger** is the event or need that starts the task. It is different from the action the actor takes. Describe a successful result and the response when the task cannot be completed.

- **Use case ID:** Optional short label, such as `UC-01`, for linking to requirements and tests.
- **Actor:** Which actor from the table above performs the task.
- **Trigger:** What makes the actor need to act *now*.
- **Task:** What the actor tries to do with OnboardAI.
- **Successful result:** What the actor can observe when the task works.
- **If it cannot work:** What the actor sees or can do when information, access, or a dependency is missing.
- **In prototype?:** Yes, no, or undecided. This is a scope decision, not a technology choice.

**Illustrative example only — not an approved OnboardAI use case:**

| Use case ID | Actor | Trigger (why now?) | Task | Successful result | If it cannot work | In prototype? |
| --- | --- | --- | --- | --- | --- | --- |
| UC-EX | New employee | Needs to check a policy before completing a task | Asks where the policy is | Opens the policy from a cited answer | Sees that no accessible source answers the question and where to ask a person | Undecided |

**Team's use cases:**

| Use case ID | Actor | Trigger (why now?) | Task | Successful result | If it cannot work | In prototype? |
| --- | --- | --- | --- | --- | --- | --- |

## Journey questions

Use these prompts after identifying the actors and use cases. They help expose missing steps and exceptions; they are not extra columns to fill for every row.

- What must a user understand before starting?
- What can they inspect or correct during the task?
- When does a person take over from the system?
- Which journeys must be demonstrated for acceptance?

**Team answers:**
