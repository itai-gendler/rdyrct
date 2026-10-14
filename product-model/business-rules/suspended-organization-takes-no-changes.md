---
appliesTo:
- type: entity
  id: link
  effect: creates
- type: entity
  id: alias
  effect: creates
- type: entity
  id: organization
  effect: changes
  facts: [Links suspended]
references:
- kind: code
  role: implementation
  target: src/worker/org-role.ts#requireOrgRole
---

# An organization whose links are suspended takes no changes

So that a suspended organization cannot make a replacement link, it refuses every change until the suspension is lifted.
