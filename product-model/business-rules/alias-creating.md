---
appliesTo:
- type: entity
  id: alias
  effect: creates
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
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
---

# Owners, admins and members add aliases

Aliases follow their link: anyone who may edit the link adds aliases to it, and a rename by such a person leaves a temporary one.
