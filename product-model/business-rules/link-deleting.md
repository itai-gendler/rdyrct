---
appliesTo:
- type: entity
  id: link
  effect: removes
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
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkRoutes
---

# Owners, admins and members delete links; platform admins delete any link

Deleting a link needs a Role above Viewer in its organization, or an AI agent acting for such a person. Platform admins delete any link from the admin console.
