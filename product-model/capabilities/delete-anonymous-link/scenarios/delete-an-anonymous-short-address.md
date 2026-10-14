---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin deletes a short address from the anonymous list
  kind: actor
  actor: platform-admin
  entities:
  - {entity: anonymous-link, effect: reads, facts: [Slug, Destination]}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product deletes it, stops it redirecting, and records the deletion in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: anonymous-link, effect: removes}
  contexts:
    web:
      place: web::admin-console::all-links
---

# Delete an anonymous short address

## Trigger

A report names an anonymous short address.

## Outcome

The address answers not found.
