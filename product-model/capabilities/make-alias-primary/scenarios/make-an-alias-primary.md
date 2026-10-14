---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Make primary on an alias
  kind: actor
  actor: user
  entities:
  - {entity: alias, effect: reads, facts: [Slug]}
  contexts:
    web:
      place: web::workspace::links
- text: The alias is still active, and when it is temporary the plan's link limit has room for one more permanent address
  kind: condition
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  - {entity: link, effect: reads, facts: []}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
- text: The Product makes the alias's slug the link's primary address and keeps the former primary address as a permanent alias
  kind: product
  actor: user
  entities:
  - {entity: link, effect: changes, facts: [Slug, Short URL]}
  - {entity: alias, effect: changes, facts: [Slug, Short URL, Origin, Expires]}
  contexts:
    web:
      place: web::workspace::links
---

# Make an alias the primary address

## Trigger

A member decides an alias is the address to share from now on.

## Outcome

Both addresses keep redirecting; the link is shown under the new one.
