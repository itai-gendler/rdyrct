---
appliesTo:
- type: entity
  id: account
  effect: changes
  to: Banned
permits:
- actors:
  - platform-admin
  when:
  - fact: Platform admin
    is: 'No'
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#validateBannedPatch
---

# Only platform admins ban, and never another platform admin

A Platform admin bans other accounts that are not Platform admins, never their own.
