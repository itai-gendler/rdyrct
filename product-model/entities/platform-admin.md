---
kind: person
acts: internal
relations:
- {entity: account, verb: uses, cardinality: one-to-one}
references:
- kind: code
  role: implementation
  target: src/worker/guards.ts#requireAdmin
- kind: code
  role: implementation
  target: src/worker/org-role.ts#orgRole
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
---

# Platform admin

The person who runs the instance. The account whose email matches the instance's configured admin address becomes the first Platform admin, and a Platform admin can make other accounts platform admins. A Platform admin passes every organization's role checks as its owner and is the only one who reaches the admin console.
