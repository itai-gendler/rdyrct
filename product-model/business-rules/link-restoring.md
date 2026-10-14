---
appliesTo:
- type: entity
  id: link
  effect: changes
  to: Active
permits:
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#setSuspended
---

# Only platform admins restore suspended links

Nobody in the organization can lift a suspension, whatever their Role.
