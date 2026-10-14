---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Revoke comp
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Comp plan]}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product clears the comp, derives the account's plan from its subscription, applies it to the organizations it owns, and records it in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: changes, facts: [Comp plan, Comp reason, Comp granted by, Comp granted at, Plan]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
---

# Revoke a comp

## Trigger

A comped arrangement ends.

## Outcome

The account is on its paid plan or Free.
