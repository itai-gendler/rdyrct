---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Platform admin]
permits:
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#validateIsAdminPatch
---

# Only platform admins grant or remove platform admin rights

A Platform admin makes other accounts Platform admins and removes the rights from others, never from themselves.
