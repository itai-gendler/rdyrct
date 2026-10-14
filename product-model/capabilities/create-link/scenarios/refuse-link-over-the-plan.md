---
kind: validation
routes:
  web: Web app
  api: REST API
steps:
- text: The User tries to create a link
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The organization's links and permanent aliases already fill the plan's link limit
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: link, effect: reads, facts: []}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
- text: The Product refuses and points to a paid plan
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::links
    api:
      place: rest-api
---

# Refuse a link over the plan's limit

## Trigger

A member of an organization at its link limit shortens another address.

## Outcome

No link is created.
