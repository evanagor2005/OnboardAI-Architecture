# Technology choices and rationale

Compare products and frameworks only after the relevant requirements, architecture rules, and component design are clear. This file replaces a separate design-decision folder.

## Selection criteria

| Criterion | Requirement / rule | Must-have or preference | Weight / priority | Evidence method |
| --- | --- | --- | --- | --- |

## Choices

| Area | Serious options | Evidence | Selected option | Why it fits / tradeoffs | Revisit trigger | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Client framework |  |  |  |  |  | Open |
| Backend language / framework | Django named by the team for the superuser and invitation account flow |  |  |  |  | Team direction; full backend choice open |
| Database |  |  |  |  |  | Open |
| Search / indexing |  |  |  |  |  | Open |
| AI model / service, if needed |  |  |  |  |  | Open |
| Identity / authorization | Django superuser and invite-created accounts for milestone 1; Keycloak or another identity provider was also suggested for later UI/UX work |  | Django superuser and invite-created accounts for milestone 1 |  | Clarify whether external identity integration remains planned | Partially decided |
| Invitation email delivery | Mailgun |  | Mailgun | Team direction; integration evidence pending | If email delivery requirements change | Team choice |
| Source integration |  |  |  |  |  | Open |
| MCP implementation, if included |  |  |  |  |  | Open |
| Hosting / deployment |  |  |  |  |  | Open |

## Evidence still needed

| Uncertain choice | Small test or research | Pass condition | Owner | Status |
| --- | --- | --- | --- | --- |
