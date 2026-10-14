---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User picks a new Role for a member
  kind: actor
  actor: user
  entities:
  - {entity: membership, effect: reads, facts: [Role]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: The member is not the owner, and members who can make changes still fit the plan's member limit
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: The Product sets the Role; a member a downgrade had demoted no longer counts as demoted
  kind: product
  actor: user
  entities:
  - {entity: membership, effect: changes, facts: [Role, Demoted]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
---

# Change a member's Role

## Trigger

An admin adjusts what a teammate may do.

## Outcome

The member has the new Role from their next request.
