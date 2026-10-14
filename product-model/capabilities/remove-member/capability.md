---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
domain: members
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
- kind: code
  role: implementation
  target: src/app/components/member-dialogs.tsx
---

# Remove member

Take someone out of the organization. The owner cannot be removed.
