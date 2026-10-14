---
kind: validation
routes:
  web: Web app
  api: REST API
steps:
- text: The User raises a Viewer to Member or Admin
  kind: actor
  actor: user
  entities:
  - {entity: membership, effect: reads, facts: [Role]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: Members who can make changes already fill the plan's member limit
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: The Product refuses and asks to set someone else to Viewer first
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
---

# Refuse write access over the plan's member limit

## Trigger

An admin of an organization over its plan restores a demoted member.

## Outcome

Nothing changes.
