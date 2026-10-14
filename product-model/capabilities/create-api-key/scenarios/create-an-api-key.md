---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User names a new API key
  kind: actor
  actor: user
  entities:
  - {entity: api-key, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::api
    api:
      place: rest-api
- text: The Product creates the key and shows the full key once
  kind: product
  actor: user
  entities:
  - {entity: api-key, effect: creates, to: Active, facts: [Name, Prefix, Key, Created]}
  contexts:
    web:
      place: web::workspace::api
    api:
      place: rest-api
---

# Create an API key

## Trigger

A person wants a script or an AI agent to act for them.

## Outcome

The person has a key to copy; a lost key has to be revoked and replaced.
