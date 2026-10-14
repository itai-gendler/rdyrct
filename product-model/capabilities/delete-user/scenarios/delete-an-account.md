---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Delete user on another account and confirms
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name, Email]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
- text: The account owns no organization
  kind: condition
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: []}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product deletes the account with its sessions and memberships, and records the deletion with its email address in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: removes, from: Banned}
  - {entity: membership, effect: removes}
  contexts:
    web:
      place: web::admin-console::users
---

# Delete an account

## Trigger

A Platform admin removes an abusive or abandoned account.

## Outcome

The account is gone; organizations it belonged to keep its links.
