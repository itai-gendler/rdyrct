---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Sign out
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace
- text: The Product ends the session and forgets what the browser kept about the person
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace
---

# Sign out

## Trigger

A person is done or on a shared computer.

## Outcome

The person is signed out and back on the public pages.
