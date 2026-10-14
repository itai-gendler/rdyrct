---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Keep forever on a temporary alias
  kind: actor
  actor: user
  entities:
  - {entity: alias, effect: reads, facts: [Slug, Expires, Recent clicks]}
  contexts:
    web:
      place: web::workspace::links
- text: The alias has not expired and the plan's link limit has room
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: link, effect: reads, facts: []}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
- text: The Product makes the alias permanent and drops its expiry
  kind: product
  actor: user
  entities:
  - {entity: alias, effect: changes, from: Temporary, to: Permanent, facts: [Expires]}
  contexts:
    web:
      place: web::workspace::links
---

# Keep a temporary alias forever

## Trigger

A member sees the old address still getting clicks and wants it to keep working.

## Outcome

The alias redirects for good.
