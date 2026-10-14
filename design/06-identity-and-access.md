# Identity and access design

## Questions

- How is a human or software caller authenticated?
- Where does permission information originate and how current is it?
- Where is policy evaluated and enforced for each path, including cached results and MCP tools?
- How are denials and failures handled without exposing restricted information?
- What is logged, and how are logs protected?

## Protected flows

| Flow | Identity source | Policy input | Enforcement point | Allowed output | Denied / failure output | Test |
| --- | --- | --- | --- | --- | --- | --- |

## Chosen design

**Team design:**

**Trust boundary diagram:**

**Linked requirements, rules, and decisions:**
