---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Comp plan, Comp reason, Comp granted by, Comp granted at]
permits:
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#writeComp
---

# Only platform admins grant and revoke comps

A comp is paid access a Platform admin gives by hand, with a reason.
