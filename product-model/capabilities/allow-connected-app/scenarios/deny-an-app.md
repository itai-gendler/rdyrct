---
kind: alternative
routes:
  web: Web app
steps:
- text: The User chooses Deny
  kind: actor
  actor: user
  entities:
  - {entity: connected-app, effect: reads, facts: [App name]}
  contexts:
    web:
      place: web::workspace::consent
- text: The Product sends the person back to the client without an allowance
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::consent
---

# Deny an AI agent client

## Trigger

A person does not recognize the client.

## Outcome

Nothing is connected.
