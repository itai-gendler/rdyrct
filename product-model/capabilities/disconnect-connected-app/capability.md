---
availability:
- {place: 'web::workspace'}
domain: api
references:
- kind: code
  role: implementation
  target: src/worker/routes/oauth-connections.ts#oauthConnectionRoutes
---

# Disconnect connected app

Remove a connected app's allowance together with every grant it holds, so it no longer acts for the person.
