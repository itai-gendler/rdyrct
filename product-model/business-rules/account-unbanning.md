---
appliesTo:
- type: entity
  id: account
  effect: changes
  to: Active
permits:
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# Only platform admins lift a ban

Nobody lifts their own ban.
