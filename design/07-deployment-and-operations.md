# Deployment, security, and operations design

## Questions

- Where will the prototype run, and what environments are needed?
- How are deployments, configuration, secrets, logs, and cost limits managed?
- What sensitive assets and trust boundaries create credible misuse or failure cases?
- What happens when a source, identity service, database, model, or network connection fails?
- What is backed up and how is restoration demonstrated?
- Who owns maintenance and recovery during the capstone?

## Runtime and risk inventory

| Component or asset | Environment / owner | Sensitive boundary or risk | Control | Failure behavior | Test |
| --- | --- | --- | --- | --- | --- |

## Chosen approach and rationale

**Team design:** Start the separate MCP service in a container managed by Docker Compose. The machine or platform running Compose, the production hosting arrangement, and how the selected company chatbot reaches the MCP endpoint remain open. The initial Compose decision does not require Django or PostgreSQL to run in containers.

**Serious alternatives and tradeoffs:**

**Deployment / trust-boundary diagram:**

**Verification / open questions:**
