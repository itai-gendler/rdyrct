---
availability:
- {place: 'web::workspace'}
- {place: mcp-server}
domain: billing
references:
- kind: code
  role: implementation
  target: src/app/routes/billing.tsx
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#getPlanUsage
- kind: code
  role: implementation
  target: src/worker/plan.ts#countActiveAddresses
---

# View plan usage

See the plan and how much of its link, member and custom domain limits the current organization uses.
