---
kind: alternative
routes:
  web: Web app
steps:
- text: The Platform admin deletes a link from the admin console's link list and confirms
  kind: actor
  actor: platform-admin
  entities:
  - {entity: link, effect: reads, facts: [Short URL]}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product deletes the link with its addresses and clicks, and records the deletion in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: link, effect: removes, from: Suspended}
  - {entity: click, effect: removes, with: link}
  contexts:
    web:
      place: web::admin-console::all-links
---

# Delete a link from the admin console

## Trigger

A Platform admin decides a reported link should not survive at all.

## Outcome

The link is gone for good and the audit log names its slug, organization and destination.
