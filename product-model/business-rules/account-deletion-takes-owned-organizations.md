---
appliesTo:
- type: entity
  id: account
  effect: removes
- type: entity
  id: organization
  effect: removes
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts#deleteAccountAndOwnedOrgs
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# Deleting an account deletes every organization it owns

An organization works within its owner's plan, so one left without its owner would have no plan and nobody able to delete it. Organizations the person only belongs to are left alone. From the admin console, an account that owns organizations cannot be deleted until they are.
