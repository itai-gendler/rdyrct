---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor asks to reset the password for their email address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product emails a reset address that lasts one hour, and says the same whether or not the address has an account
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::public::sign-in
- text: The Visitor opens the email and enters a new password twice
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::reset-password
- text: The Product sets the new password and sends the person to sign in
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::reset-password
---

# Reset a forgotten password

## Trigger

A person forgot their password.

## Outcome

The password is changed and the person can sign in with it.
