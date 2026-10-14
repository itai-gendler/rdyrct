---
kind: primary
routes:
  web: Web app
steps:
- text: The User removes an alias and confirms
  kind: actor
  actor: user
  entities:
  - {entity: alias, effect: reads, facts: [Slug, Recent clicks, Last use]}
  contexts:
    web:
      place: web::workspace::links
- text: The Product retires the alias, stops it redirecting and frees its slug, keeping it for its click history
  kind: product
  actor: user
  entities:
  - {entity: alias, effect: changes, from: Permanent, to: Retired, facts: []}
  - {entity: click, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::links
---

# Remove an alias

## Trigger

A member no longer wants an extra address to work.

## Outcome

The alias answers not found; its past clicks stay in the link's analytics.
