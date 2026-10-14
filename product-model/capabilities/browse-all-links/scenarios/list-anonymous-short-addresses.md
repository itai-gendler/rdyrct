---
kind: alternative
routes:
  web: Web app
steps:
- text: The Platform admin switches to the anonymous list
  kind: actor
  actor: platform-admin
  entities: []
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product lists the newest short addresses made without an account, with their destinations, expiry and risk score
  kind: product
  actor: platform-admin
  entities:
  - {entity: anonymous-link, effect: reads, facts: [Slug, Destination, Expires, Risk score]}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::all-links
---

# List anonymous short addresses

## Trigger

A report names an address that belongs to no organization.

## Outcome

The Platform admin sees it in one place.
