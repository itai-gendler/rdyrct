---
kind: validation
routes:
  web: Web app
steps:
- text: The Visitor enters the email address and password of a banned account
  kind: actor
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web::public::sign-in
- text: The account is banned
  kind: condition
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::public::sign-in
- text: The Product refuses the session and says the account is suspended
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web::public::sign-in
---

# A banned account cannot sign in

## Trigger

Someone tries to sign in to an account a Platform admin banned.

## Outcome

No session starts.
