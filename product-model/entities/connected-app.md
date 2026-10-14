---
domain: api
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#oauthConsent
- kind: code
  role: implementation
  target: src/worker/routes/oauth-connections.ts#oauthConnectionRoutes
---

# Connected app

An AI agent client a person allowed to act for them through the MCP server's sign-in, listed under Connected apps until they disconnect it.

## Information kept

- **App name** — the client's name, from its published client metadata
- **Scopes** — what the person allowed it to ask for
- **Connected** — when the person allowed it
