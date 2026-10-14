---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Ban user on an account that is not a Platform admin and confirms
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name, Platform admin]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product bans the account, ends its sessions, and records the ban in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: changes, from: Active, to: Banned, facts: []}
  contexts:
    web:
      place: web::admin-console::users
---

# Ban an account

## Trigger

An account is used for abuse.

## Outcome

The person is signed out everywhere and refused at sign-in; API keys and AI agents acting for them are refused too.
