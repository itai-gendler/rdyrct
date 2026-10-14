---
availability:
- {place: 'web::workspace'}
domain: api
references:
- kind: code
  role: implementation
  target: src/app/routes/consent.tsx
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
- kind: code
  role: implementation
  target: src/worker/mcp-oauth.ts
---

# Allow connected app

Allow an AI agent client to act for the person through the MCP server. The client starts the sign-in; the person signs in if needed and sees which client is asking and for what.
