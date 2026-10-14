---
appliesTo:
- type: entity
  id: link
  effect: changes
  to: Suspended
- type: entity
  id: link
  effect: changes
  to: Active
- type: entity
  id: link
  effect: changes
  facts: [Risk score]
  contexts:
  - place: web::admin-console::all-links
- type: entity
  id: link
  effect: removes
  contexts:
  - place: web::admin-console::all-links
- type: entity
  id: anonymous-link
  effect: removes
  contexts:
  - place: web::admin-console::all-links
- type: entity
  id: organization
  effect: removes
  contexts:
  - place: web::admin-console::organizations
- type: entity
  id: account
  effect: changes
  to: Banned
- type: entity
  id: account
  effect: changes
  to: Active
- type: entity
  id: account
  effect: changes
  facts: [Comp plan]
- type: entity
  id: account
  effect: removes
  contexts:
  - place: web::admin-console::users
- type: entity
  id: audit-entry
references:
- kind: code
  role: implementation
  target: src/worker/audit.ts#recordAdminAction
---

# Every moderation and account action in the admin console is recorded in the audit log

Suspending, restoring, re-checking and deleting links, deleting anonymous short addresses and organizations, suspending an organization's links, banning, unbanning, comps and deleting accounts each add an audit entry with enough detail to read once the target is gone.
