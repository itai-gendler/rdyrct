---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Unban user and confirms
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product lifts the ban and records it in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: changes, from: Banned, to: Active, facts: []}
  contexts:
    web:
      place: web::admin-console::users
---

# Unban an account

## Trigger

A ban was a mistake or an appeal succeeded.

## Outcome

The person can sign in again.
