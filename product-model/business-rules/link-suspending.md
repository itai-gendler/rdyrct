---
appliesTo:
- type: entity
  id: link
  effect: changes
  to: Suspended
permits:
- actors:
  - platform-admin
- unattended: true
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#setSuspended
- kind: code
  role: implementation
  target: src/worker/abuse.ts#suspendOrgLinks
---

# Only platform admins and the abuse control suspend links

Suspension is a moderation decision. A Platform admin suspends one link with a reason; the Product suspends every link of a new free organization that floods the redirect path.
