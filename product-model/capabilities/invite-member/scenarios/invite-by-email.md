---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User enters one or more email addresses and a Role
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: Members plus open invites plus the new ones fit the plan's member limit
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
- text: The Product creates one invite per address, valid for seven days
  kind: product
  actor: user
  entities:
  - {entity: invite, effect: creates, facts: [Role, Email, Invite link, Created, Expires]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
- text: The Product emails each address an invitation to join the organization
  kind: product
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: [Email, Invite link]}
  - {entity: organization, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::members
    api:
      place: rest-api
---

# Invite people by email

## Trigger

An admin brings teammates in.

## Outcome

Each person has an email to join with the chosen Role, and the invites are pending.

## Edge cases

- Malformed and repeated addresses are dropped.
