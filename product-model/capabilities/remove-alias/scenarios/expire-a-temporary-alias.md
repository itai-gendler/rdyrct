---
kind: edge
routes:
  web: Web app
steps:
- text: 48 hours have passed since a rename left a temporary alias
  kind: condition
  unattended: true
  entities:
  - {entity: alias, effect: reads, facts: [Expires]}
  contexts:
    web:
      place: web::workspace::links
- text: The Product stops redirecting the alias at once and retires it in its daily sweep, freeing the slug
  kind: product
  entities:
  - {entity: alias, effect: changes, from: Temporary, to: Retired, facts: []}
  contexts:
    web:
      place: web::workspace::links
---

# A temporary alias expires

## Trigger

The 48 hours after a rename run out.

## Outcome

The old address answers not found and its slug can be used again.
