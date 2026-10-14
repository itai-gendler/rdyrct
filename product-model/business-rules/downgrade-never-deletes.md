---
appliesTo:
- type: entity
  id: organization
  effect: changes
  to: Locked
- type: entity
  id: membership
  effect: changes
  facts: [Demoted]
- type: entity
  id: custom-domain
  effect: changes
  facts: [Locked]
references:
- kind: code
  role: implementation
  target: src/worker/reconcile.ts#reconcileUser
---

# A plan change never deletes anything

Going down a plan locks organizations, demotes members to Viewer and locks custom domains beyond the new plan, oldest kept; it deletes nothing and never demotes the owner. Going back up restores every Role and lock it changed.
