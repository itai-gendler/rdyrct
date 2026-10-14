---
kind: edge
routes:
  web: Web app
steps:
- text: Seven days passed since an invite was created and nobody used it
  kind: condition
  unattended: true
  entities:
  - {entity: invite, effect: reads, facts: [Expires]}
  contexts:
    web:
      place: web::workspace::members
- text: The Product stops accepting it and deletes it in its daily sweep
  kind: product
  entities:
  - {entity: invite, effect: removes}
  contexts:
    web:
      place: web::workspace::members
---

# An invite expires unused

## Trigger

An invite's week runs out.

## Outcome

The invite and the address it was sent to are gone.
