---
appliesTo:
- type: entity
  id: alias
  effect: changes
permits:
- related:
  - {verb: has, entity: link}
  - {verb: has, entity: organization}
  - {verb: has, entity: membership}
  - {verb: holds, entity: user}
  when:
  - entity: membership
    fact: Role
    is-not: Viewer
- actors:
  - platform-admin
- unattended: true
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
---

# Owners, admins and members keep, promote and remove aliases

Anyone who may edit the link keeps its temporary aliases forever, makes one primary or removes one. The Product retires temporary aliases on its own when they expire.
