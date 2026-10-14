---
appliesTo:
- type: entity
  id: organization
  effect: changes
  facts: [QR defaults]
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
  target: src/app/components/qr-defaults-card.tsx
---

# Only owners and admins change the QR defaults

The organization's QR defaults are set by its owner or an admin.
