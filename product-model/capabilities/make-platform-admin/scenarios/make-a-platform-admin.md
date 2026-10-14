---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Make platform admin on another account and confirms
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name, Platform admin]}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product makes the account a Platform admin
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: changes, facts: [Platform admin]}
  contexts:
    web:
      place: web::admin-console::users
---

# Make an account a Platform admin

## Trigger

The instance needs a second administrator.

## Outcome

The account reaches the admin console and acts as owner in every organization.
