---
kind: primary
routes:
  web: Web app
steps:
- text: The User changes their name, or picks or removes a picture, and saves
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Name, Picture]}
  contexts:
    web:
      place: web::workspace::settings
- text: The Product saves whichever changed
  kind: product
  actor: user
  entities:
  - {entity: account, effect: changes, facts: [Name, Picture]}
  contexts:
    web:
      place: web::workspace::settings
---

# Change name or picture

## Trigger

A person wants teammates to recognize them.

## Outcome

The new name and picture show across the app.
