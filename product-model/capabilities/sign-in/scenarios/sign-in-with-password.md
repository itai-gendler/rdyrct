---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor enters their email address and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The password matches an active account with a confirmed address
  kind: condition
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email, Email verified]}
  contexts:
    web:
      place: web::public::sign-in
- text: The Product starts a session and takes the person on to the page they were going to, the dashboard by default
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email]}
  contexts:
    web:
      place: web::public::sign-in
---

# Sign in with email and password

## Trigger

A person with an account wants to use the app.

## Outcome

The person is signed in.
