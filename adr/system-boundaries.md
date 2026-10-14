# Architecture rules — system boundaries

Derive rules from accepted scope and software requirements. Keep implementation choices in design files.

## Questions

- What responsibilities shall belong to OnboardAI versus source systems, users, and external services?
- Which information and operations shall cross each boundary?
- Where shall trust or permission context be established and carried?
- What shall remain functional when an external dependency fails?
- Which boundaries must be explicit so components can be changed independently?

## Rules

| ID | Shall statement | Source requirement(s) | Applies to | Verification method | Status |
| --- | --- | --- | --- | --- | --- |
