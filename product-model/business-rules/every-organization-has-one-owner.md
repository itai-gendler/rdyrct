---
appliesTo:
- type: entity
  id: membership
  effect: creates
- type: entity
  id: membership
  effect: changes
  facts: [Role]
references:
- kind: code
  role: implementation
  target: src/worker/plan.ts#createOwnedOrg
- kind: code
  role: implementation
  target: src/shared/types.ts#INVITABLE_ROLES
---

# Every organization has exactly one owner

The owner is whoever created the organization. Nobody is invited as Owner and the owner's Role never changes.
