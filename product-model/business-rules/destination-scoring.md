---
appliesTo:
- type: entity
  id: link
  effect: changes
  facts: [Risk score, Risk reasons, Risk checked]
permits:
- related:
  - &id001 {verb: has, entity: organization}
  - &id002 {verb: has, entity: membership}
  - &id003 {verb: holds, entity: user}
  when:
  - &id004
    entity: membership
    fact: Role
    is-not: Viewer
- related:
  - *id001
  - *id002
  - *id003
  - {verb: connects, entity: ai-agent}
  when:
  - *id004
- actors:
  - platform-admin
- unattended: true
references:
- kind: code
  role: implementation
  target: src/worker/risk.ts#scoreAndRecord
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkRoutes
---

# Destination risk is scored by the Product and re-checked only by platform admins

The check runs on its own after whoever may create or edit a link creates it or changes its destination; nobody sets a score by hand. Platform admins re-check a destination on demand.
