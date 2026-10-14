---
kind: edge
routes:
  web: Web app
steps:
- text: A day has passed since the short address was made and nobody kept it by signing up
  kind: condition
  unattended: true
  entities:
  - {entity: anonymous-link, effect: reads, facts: [Expires]}
  contexts:
    web:
      place: web::public::home
- text: The Product stops redirecting it and removes it in its daily sweep
  kind: product
  entities:
  - {entity: anonymous-link, effect: removes}
  contexts:
    web:
      place: web::public::home
---

# An unclaimed short address expires

## Trigger

The 24 hours of an anonymous short address run out.

## Outcome

The address answers not found and the slug is free again.
