---
kind: validation
routes:
  web: Web app
  api: REST API
steps:
- text: The User invites more people
  kind: actor
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: Members plus open invites would exceed the plan's member limit
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: invite, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: The Product refuses and points to a paid plan on Free
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
---

# Refuse invites over the plan's member limit

## Trigger

An admin of a full organization invites someone.

## Outcome

Nobody is invited.
