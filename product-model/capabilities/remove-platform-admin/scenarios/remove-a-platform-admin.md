---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Remove platform admin on another account and confirms
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name, Platform admin]}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product removes the account's Platform admin rights
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: changes, facts: [Platform admin]}
  contexts:
    web:
      place: web::admin-console::users
---

# Remove an account's Platform admin rights

## Trigger

An administrator steps down.

## Outcome

The account is an ordinary account again.
