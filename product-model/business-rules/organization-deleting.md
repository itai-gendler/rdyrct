---
appliesTo:
- type: entity
  id: organization
  effect: removes
permits:
- related:
  - {verb: has, entity: membership}
  - {verb: holds, entity: user}
  when:
  - entity: membership
    fact: Role
    is: Owner
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
---

# Only the owner deletes an organization

Deleting an organization is the owner's alone, including by deleting their account. Platform admins delete any organization.
