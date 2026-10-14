---
entities:
- {entity: api-key, shows: [Name, Prefix, Key, Created, Last used], collects: [Name]}
- {entity: connected-app, shows: [App name, Scopes, Connected]}
entryPoints:
- web: /api-keys
references:
- kind: code
  role: implementation
  target: src/app/routes/api-keys.tsx
---

# API

The person's API keys and connected apps, with how to connect an AI agent to the MCP server.
