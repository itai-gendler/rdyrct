---
appliesTo:
- type: entity
  id: custom-domain
  effect: creates
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

# Only owners and admins add custom domains

Adding a custom domain needs the Owner or Admin Role; members and viewers do not see the controls.
