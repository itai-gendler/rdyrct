---
kind: edge
routes:
  web: Web app
steps:
- text: The User chooses Keep forever on a temporary alias
  kind: actor
  actor: user
  entities:
  - {entity: alias, effect: reads, facts: [Slug]}
  contexts:
    web:
      place: web::workspace::links
- text: The alias already expired
  kind: condition
  actor: user
  entities:
  - {entity: alias, effect: reads, facts: [Expires]}
  contexts:
    web:
      place: web::workspace::links
- text: The Product says the address already expired
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::links
---

# Too late to keep an alias

## Trigger

A member acts after the 48 hours ran out.

## Outcome

Nothing changes.
