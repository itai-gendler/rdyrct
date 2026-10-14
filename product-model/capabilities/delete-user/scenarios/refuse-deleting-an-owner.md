---
kind: validation
routes:
  web: Web app
steps:
- text: The Platform admin deletes an account
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::admin-console::users
- text: The account owns at least one organization
  kind: condition
  actor: platform-admin
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product refuses and asks to delete those organizations first
  kind: product
  actor: platform-admin
  entities:
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
---

# Refuse deleting an account that owns organizations

## Trigger

A Platform admin deletes the owner of an organization.

## Outcome

Nothing is deleted.
