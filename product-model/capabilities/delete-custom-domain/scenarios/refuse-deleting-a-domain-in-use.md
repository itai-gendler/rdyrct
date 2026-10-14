---
kind: validation
routes:
  web: Web app
  api: REST API
steps:
- text: The User deletes a custom domain
  kind: actor
  actor: user
  entities:
  - {entity: custom-domain, effect: reads, facts: [Hostname]}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
- text: Links or aliases still live on it
  kind: condition
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Domain]}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
- text: The Product refuses and asks to move or delete those links first
  kind: product
  actor: user
  entities:
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::domains
    api:
      place: rest-api
---

# Refuse deleting a custom domain links still use

## Trigger

An admin deletes a custom domain that still carries links.

## Outcome

Nothing changes.
