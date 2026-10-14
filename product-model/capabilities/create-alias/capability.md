---
availability:
- {place: 'web::workspace'}
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#assertAliasQuota
- kind: code
  role: implementation
  target: src/worker/plan.ts#insertAddressWithinLimit
- kind: code
  role: implementation
  target: src/app/components/create-alias-dialog.tsx
---

# Create alias

Add another address to a link on its own domain. A link holds at most five aliases, and each permanent alias counts toward the plan's link limit.
