---
kind: alternative
routes:
  web: Web app
steps:
- text: The Visitor chooses to continue with Google and approves at Google
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product starts a session for the account with that address
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::public::sign-in
---

# Sign in with Google

## Trigger

A person who uses Google sign-in comes back; offered only where the instance has it configured.

## Outcome

The person is signed in.
