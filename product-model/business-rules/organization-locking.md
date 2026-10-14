---
appliesTo:
- type: entity
  id: organization
  effect: changes
  to: Locked
permits:
- related:
  - {verb: has, entity: membership}
  - {verb: holds, entity: user}
  when:
  - entity: membership
    fact: Role
    is: Owner
- actors:
  - platform-admin
- unattended: true
references:
- kind: code
  role: implementation
  target: src/worker/reconcile.ts#reconcileUser
- kind: code
  role: implementation
  target: src/worker/plan.ts#keepOrgActive
---

# Organizations are locked only by a plan change or the owner's pick

The Product locks the organizations beyond the owner's plan; the owner's pick of another organization to keep active locks one in its place.
