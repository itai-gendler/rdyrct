---
availability:
- {place: 'web::admin-console'}
references:
- kind: code
  role: implementation
  target: src/worker/abuse.ts#sweepAbusiveOrgs
- kind: code
  role: implementation
  target: src/worker/abuse.ts#suspendOrgLinks
- kind: doc
  role: context
  target: docs/incidents/2026-09-10-queue-ops-exhaustion.md
---

# Suspend an organization's links

When a newly created free organization's links pass the free plan's daily redirect ceiling, the Product suspends all of them at once, closes the organization to changes, and emails the owner and the Platform admin. Nothing is deleted.
