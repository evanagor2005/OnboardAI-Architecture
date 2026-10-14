# Integrated system map

Complete this after the component designs, then keep it aligned with accepted changes.

## System overview

What are the accepted components, responsibilities, data stores, external systems, and user entry points?

**Team design:**

## End-to-end flows

| Flow | Starting actor | Components and data crossed | Authorization points | Expected result | Failure path | Diagram |
| --- | --- | --- | --- | --- | --- | --- |

Consider only flows included in scope, such as adding or updating knowledge, answering a question, following an onboarding path, and calling an MCP tool.

## Trust and dependency review

- Does every external boundary have an owner and failure behavior?
- Does every path returning knowledge enforce the accepted access rules?
- Does each stored or derived item retain the provenance required for citations and deletion?
- Do the component designs and technology selections fit this map?

**Open contradictions:**

**Editable diagrams:**
