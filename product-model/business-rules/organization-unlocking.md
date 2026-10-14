---
appliesTo:
- type: entity
  id: organization
  effect: changes
  to: Active
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
  target: src/worker/routes/orgs.ts#orgRoutes
- kind: code
  role: implementation
  target: src/worker/plan.ts#keepOrgActive
---

# Only the owner picks which organization stays active

When an owner holds more organizations than the plan covers, the owner, and nobody else in those organizations, picks the one that stays active. The Product unlocks organizations on its own when the plan covers them again.
