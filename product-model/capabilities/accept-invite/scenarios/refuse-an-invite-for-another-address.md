---
kind: validation
routes:
  web: Web app
steps:
- text: The User accepts an emailed invite while signed in with a different address
  kind: actor
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::invite
- text: The invite was sent to another address
  kind: condition
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::workspace::invite
- text: The Product refuses and asks the person to sign in with the invited address
  kind: product
  actor: user
  entities:
  - {entity: invite, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::invite
---

# Refuse an emailed invite from another account

## Trigger

A person opens an invite meant for their other address.

## Outcome

Nothing changes and the invite stays usable.
