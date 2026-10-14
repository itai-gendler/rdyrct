---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User removes a member and confirms
  kind: actor
  actor: user
  entities:
  - {entity: membership, effect: reads, facts: [Role]}
  - {entity: account, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: The member is not the owner
  kind: condition
  actor: user
  entities:
  - {entity: membership, effect: reads, facts: [Role]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: The Product removes the membership; the person keeps their account and the links they made stay in the organization
  kind: product
  actor: user
  entities:
  - {entity: membership, effect: removes}
  - {entity: account, effect: reads, facts: []}
  - {entity: organization, effect: reads, facts: []}
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
---

# Remove a member

## Trigger

Someone leaves the team.

## Outcome

The person no longer reaches the organization, and a seat is free.
