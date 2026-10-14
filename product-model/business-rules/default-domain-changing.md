---
appliesTo:
- type: entity
  id: organization
  effect: changes
  facts: [Default domain]
permits:
- related:
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
  target: src/worker/routes/orgs.ts#orgRoutes
---

# Only owners and admins choose the default domain

Which custom domain new links start on is an organization setting for owners and admins.
