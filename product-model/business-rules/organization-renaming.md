---
appliesTo:
- type: entity
  id: organization
  effect: changes
  facts: [Name]
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
  target: src/app/routes/organization.tsx#OrganizationPage
---

# Only the owner renames the organization

The organization's name is the owner's to change.
