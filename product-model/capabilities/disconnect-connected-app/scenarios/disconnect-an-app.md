---
kind: primary
routes:
  web: Web app
steps:
- text: The User disconnects a connected app and confirms
  kind: actor
  actor: user
  entities:
  - {entity: connected-app, effect: reads, facts: [App name]}
  contexts:
    web:
      place: web::workspace::api
- text: The Product removes the allowance and every grant the client holds from it
  kind: product
  actor: user
  entities:
  - {entity: connected-app, effect: removes}
  contexts:
    web:
      place: web::workspace::api
---

# Disconnect a connected app

## Trigger

A person stops using an AI agent client.

## Outcome

The client is gone from Connected apps and cannot reconnect without asking again.
