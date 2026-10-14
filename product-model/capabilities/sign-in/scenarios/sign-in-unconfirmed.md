---
kind: alternative
routes:
  web: Web app
steps:
- text: The Visitor enters the email address and password of an account whose address is not confirmed
  kind: actor
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web::public::sign-in
- text: The Product emails a six-digit code and asks for it
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [Email, Email verified]}
  contexts:
    web:
      place: web::public::sign-in
- text: The Visitor enters the code
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product marks the address confirmed and starts a session
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: changes, facts: [Email verified]}
  contexts:
    web:
      place: web::public::sign-in
---

# Sign in before confirming the address

## Trigger

A person signs in on an instance that sends email before ever entering their code.

## Outcome

The address is confirmed and the person is signed in.
