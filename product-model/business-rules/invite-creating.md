---
appliesTo:
- type: entity
  id: invite
  effect: creates
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
  - &id005
    entity: membership
    fact: Role
    is-not: Member
- related:
  - *id001
  - *id002
  - *id003
  - {verb: connects, entity: ai-agent}
  when:
  - *id004
  - *id005
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
- kind: code
  role: implementation
  target: src/shared/types.ts#INVITABLE_ROLES
---

# Only owners and admins invite people

Inviting needs the Owner or Admin Role, including through an AI agent acting for such a person. Nobody can be invited as Owner.
