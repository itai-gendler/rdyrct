---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
domain: api
references:
- kind: code
  role: implementation
  target: src/worker/routes/api-keys.ts#apiKeyRoutes
- kind: code
  role: implementation
  target: src/worker/api-keys.ts
- kind: code
  role: implementation
  target: src/app/routes/api-keys.tsx
---

# Create API key

Create a named API key for a program or AI agent that has no browser session. The full key is shown once; only its start is kept to tell keys apart.
