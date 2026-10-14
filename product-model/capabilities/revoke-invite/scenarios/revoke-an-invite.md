---
kind: primary
routes:
  web: Web app
steps:
- text: The User revokes a pending invite
  kind: actor
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: [Email, Role]}
  contexts:
    web:
      place: web::workspace::members
- text: The Product deletes the invite, freeing its seat
  kind: product
  actor: user
  entities:
  - {entity: invite, effect: removes}
  contexts:
    web:
      place: web::workspace::members
---

# Revoke a pending invite

## Trigger

An admin invited the wrong person or changed their mind.

## Outcome

Opening the invite answers not found.
