---
kind: edge
routes:
  web: Web app
steps:
- text: The Visitor submits an email address that already has an account
  kind: actor
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web::public::sign-up
- text: An account with that address exists
  kind: condition
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email, Email verified]}
  contexts:
    web:
      place: web::public::sign-up
- text: The Product answers exactly as for a new sign-up, creates nothing, and emails the address's owner that someone tried to sign up with it
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::public::sign-up
---

# Sign up with an address that already has an account

## Trigger

Someone signs up with an address that is already in use.

## Outcome

No second account exists; only the inbox owner learns of the attempt.
