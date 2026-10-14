---
appliesTo:
- type: entity
  id: custom-domain
  effect: changes
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
  target: src/worker/routes/domains.ts#domainRoutes
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#probeDomain
---

# Only owners and admins change custom domains

Owners and admins change a custom domain's root redirect. The Product moves a custom domain through its setup and locks or unlocks it after plan changes.
