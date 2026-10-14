---
appliesTo:
- type: entity
  id: invite
  effect: removes
  contexts:
  - place: web::workspace::members
  - place: rest-api
permits:
- related:
  - {verb: has, entity: organization}
  - {verb: has, entity: membership}
  - {verb: holds, entity: user}
  when:
  - entity: membership
    fact: Role
    is-not: Viewer
  - entity: membership
    fact: Role
    is-not: Member
- actors:
  - platform-admin
- unattended: true
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#sweepExpiredInvites
---

# Only owners and admins revoke invites

Pending invites are listed and withdrawn by owners and admins; the Product removes those whose seven days are over.
