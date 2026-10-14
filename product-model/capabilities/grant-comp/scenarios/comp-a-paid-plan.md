---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Comp a paid plan, picks Hobby or Pro and writes a reason
  kind: actor
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name, Comp plan]}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product records the comp with who granted it and when, derives the account's plan, applies it to the organizations it owns, and records the grant in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: changes, facts: [Comp plan, Comp reason, Comp granted by, Comp granted at, Plan]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
---

# Comp a paid plan

## Trigger

A Platform admin gives a partner or a support case paid access.

## Outcome

The account has the comped plan whatever its subscription says.

## Edge cases

- A comp without a reason, or with a reason over 500 characters, is refused.
