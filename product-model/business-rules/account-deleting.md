---
appliesTo:
- type: entity
  id: account
  effect: removes
permits:
- related:
  - {verb: uses, entity: user}
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts#deleteAccountAndOwnedOrgs
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# A person deletes their own account; platform admins delete others

A Platform admin never deletes their own account from the admin console.
