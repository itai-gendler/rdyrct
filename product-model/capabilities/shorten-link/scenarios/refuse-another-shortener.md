---
kind: validation
routes:
  web: Web app
steps:
- text: The Visitor submits an address on a known URL shortener's host
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::home
- text: The address points at another URL shortener
  kind: condition
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::home
- text: The Product refuses it and asks for the final address instead
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::home
---

# Refuse a destination that is another URL shortener

## Trigger

A Visitor pastes an address that is itself a short address from another service.

## Outcome

Nothing is created; the Visitor is told to point at the final address.
