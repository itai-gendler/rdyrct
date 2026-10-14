---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
- {place: mcp-server}
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
- kind: code
  role: implementation
  target: src/app/routes/link-detail.tsx
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#getLinkStats
---

# View link analytics

See one link's clicks over the plan's window: totals, clicks per day, countries, referrers, devices and the latest click.
