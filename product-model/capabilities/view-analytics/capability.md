---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
- {place: mcp-server}
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#computeWindows
- kind: code
  role: implementation
  target: src/app/routes/analytics.tsx
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#getOrgStats
---

# View analytics

See the organization's clicks over a window up to the plan's limit (7 days on Free, 30 on Hobby, 365 on Pro), or hour by hour over the last day.
