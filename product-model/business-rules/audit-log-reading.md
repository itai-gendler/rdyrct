---
appliesTo:
- type: entity
  id: audit-entry
  effect: reads
permits:
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# Only platform admins read the audit log

The audit log is part of the admin console.
