---
kind: primary
routes:
  web: Web app
steps:
- text: The User enters a new name of at most 100 characters and saves
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::organization
- text: The Product saves the name
  kind: product
  actor: user
  entities:
  - {entity: organization, effect: changes, facts: [Name]}
  contexts:
    web:
      place: web::workspace::organization
---

# Rename the organization

## Trigger

The owner wants the organization called something else.

## Outcome

Everyone in the organization sees the new name.
