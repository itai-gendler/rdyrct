---
appliesTo:
- type: entity
  id: link
  effect: changes
- type: entity
  id: custom-domain
  effect: changes
- type: entity
  id: membership
  effect: changes
- type: entity
  id: invite
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/org-role.ts#requireOrgRole
---

# A locked organization takes no changes

While locked, an organization refuses every change from everyone, its owner included, and keeps serving its links. Deleting it and picking it as the organization to keep active remain possible.
