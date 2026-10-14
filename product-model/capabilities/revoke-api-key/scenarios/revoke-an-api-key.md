---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User revokes one of their API keys
  kind: actor
  actor: user
  entities:
  - {entity: api-key, effect: reads, facts: [Name, Prefix]}
  contexts:
    web:
      place: web::workspace::api
    api:
      place: rest-api
- text: The Product revokes the key and drops it from the list
  kind: product
  actor: user
  entities:
  - {entity: api-key, effect: changes, from: Active, to: Revoked, facts: []}
  contexts:
    web:
      place: web::workspace::api
    api:
      place: rest-api
---

# Revoke an API key

## Trigger

A key leaked or is no longer needed.

## Outcome

Requests with the key are refused from now on.
