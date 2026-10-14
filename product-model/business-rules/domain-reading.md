---
appliesTo:
- type: entity
  id: custom-domain
  effect: reads
  contexts:
  - place: web::workspace::domains
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
---

# Only owners and admins see the custom domain list

The Domains page and its status checks are for owners and admins; everyone else in the organization sees links on custom domains but not the domains' setup.
