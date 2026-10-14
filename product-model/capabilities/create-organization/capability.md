---
availability:
- {place: 'web::workspace'}
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
- kind: code
  role: implementation
  target: src/worker/plan.ts#createOwnedOrg
- kind: code
  role: implementation
  target: src/app/routes/shell.tsx
---

# Create organization

Create another organization the person owns. Only Pro covers more than one owned organization.
