---
type: api
actors:
- user
entryPoints:
- api: /api/orgs/:orgId
references:
- kind: code
  role: implementation
  target: src/app/routes/docs.tsx#DocsPage
- kind: code
  role: implementation
  target: src/worker/session.ts#withSession
---

# REST API

The documented organization routes, answering to an API key exactly as they answer to a signed-in browser: the key resolves to its person, and their Role in each organization decides what they may do.
