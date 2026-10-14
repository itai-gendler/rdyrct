---
availability:
- {place: 'web::workspace'}
references:
- kind: code
  role: implementation
  target: src/app/routes/dashboard.tsx
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
---

# View dashboard

See the current organization at a glance: click totals, the latest clicks and the latest links, with a quick way to shorten a link. Until the organization has a link, the dashboard asks for one.
