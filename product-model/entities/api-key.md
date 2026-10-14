---
domain: api
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#apiKeys
- kind: code
  role: implementation
  target: src/worker/routes/api-keys.ts#apiKeyRoutes
---

# API key

A credential a person creates for a program with no browser session, such as a script calling the REST API or an AI agent calling the MCP server. It acts as that person in every organization they belong to.

## Information kept

- **Name** — a label to tell keys apart
- **Prefix** — the start of the key, shown in the list
- **Key** — the full key, shown once when it is created
- **Created** — when it was created
- **Last used** — when it last authenticated a request

## States

### Active

The key authenticates requests.

### Revoked

The key is refused from its next request on.
