---
appliesTo:
- type: entity
  id: membership
  effect: removes
  contexts:
  - place: web::workspace::members
  - place: rest-api
  - place: web::admin-console::users
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
  - fact: Role
    is-not: Owner
- actors:
  - platform-admin
  when:
  - fact: Role
    is-not: Owner
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#assertMember
---

# Only owners and admins remove members, and never the owner

An owner or admin takes anyone but the owner out of the organization; a Platform admin deleting an account takes it out of every organization. Memberships also go when their organization is deleted.
