# Architecture workshop guide

Use this guide to fill the repository with team decisions. The order protects the distinction between **what is required** and **how it is built**; revisit an earlier file when a later discussion reveals a conflict.

## Before the meeting

1. Have every teammate skim the [document sequence](README.md) and the templates for their assigned areas. The [original question bank](reference/workshop-questions/00-index.md) is optional background.
2. Bring known course constraints, deadlines, data restrictions, team skills, and candidate technology options. Treat candidate options as inputs to discussion, not decisions.
3. Choose a facilitator, a recorder, and a method for resolving disagreement.

## During the meeting

| Pass | Files | Exit condition |
| --- | --- | --- |
| 1. Commitments | [`sow/`](sow/statement-of-work.md) | Intended users, prototype boundaries, deliverables, and acceptance authority are stated. |
| 2. Behavior | [`requirements/`](requirements/README.md) | Each included journey and quality constraint has a testable requirement or an explicit open issue. |
| 3. Architecture rules | [`adr/`](adr/README.md) | Components and boundaries have traceable, technology-neutral shall rules. |
| 4. Design and technology | [`design/`](design/README.md), [`design-decisions/`](design-decisions/README.md) | The team has a coherent data model, component and interface design, technology comparison, and rationale for significant choices. |
| 5. Proof | [`verification/`](verification/README.md) | Every accepted requirement and rule has a verification method and acceptance target. |
| 6. Reconcile | [`traceability.md`](traceability.md), [`design/14-system-map.md`](design/14-system-map.md) | Links, diagrams, and system boundaries match the accepted decisions. |

For each item: **read the question → discuss options → write the team's answer → record why when the tradeoff matters → assign an owner for anything still open**. Use [`open-issues.md`](open-issues.md) when evidence is missing. Mark a file **Not applicable to prototype** if its capability was excluded in the SOW. Do not fill a blank with a guess to make the file look complete.

## At the end

Review the root [README](README.md), traceability matrix, architecture rules, selected technologies, verification plan, and open issues together. Commit the files as the team's agreed baseline, with status labels that distinguish accepted, proposed, and open material.
