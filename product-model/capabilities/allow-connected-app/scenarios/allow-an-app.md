---
kind: primary
routes:
  web: Web app
steps:
- text: The User reviews which client is asking and for what, and chooses Allow
  kind: actor
  actor: user
  entities:
  - {entity: connected-app, effect: reads, facts: [App name, Scopes]}
  contexts:
    web:
      place: web::workspace::consent
- text: The Product records the allowance and sends the person back to the client, which can now call the MCP server as them
  kind: product
  actor: user
  entities:
  - {entity: connected-app, effect: creates, facts: [App name, Scopes, Connected]}
  contexts:
    web:
      place: web::workspace::consent
---

# Allow an AI agent client

## Trigger

A person connects their AI chatbot to rdyrct.

## Outcome

The client is listed under Connected apps and its tool calls act as the person.
