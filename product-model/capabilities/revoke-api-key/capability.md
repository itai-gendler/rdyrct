---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
domain: api
references:
- kind: code
  role: implementation
  target: src/worker/routes/api-keys.ts#apiKeyRoutes
---

# Revoke API key

Revoke an API key. Its next request is refused, wherever it is used.
