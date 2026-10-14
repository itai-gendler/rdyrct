---
appliesTo:
- type: entity
  id: custom-domain
  effect: removes
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
references:
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#domainRoutes
---

# Only owners and admins delete custom domains

Deleting a custom domain needs the Owner or Admin Role. A custom domain also goes when its organization is deleted.
