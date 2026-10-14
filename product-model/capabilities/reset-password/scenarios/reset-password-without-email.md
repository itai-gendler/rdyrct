---
kind: edge
routes:
  web: Web app
steps:
- text: The Visitor asks to reset their password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The instance has no email provider
  kind: condition
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product says passwords cannot be reset by email on this instance
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
---

# Reset is unavailable without email

## Trigger

A person asks for a reset on an instance with no email provider.

## Outcome

Nothing is sent.
