---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Restore link on a suspended link
  kind: actor
  actor: platform-admin
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Suspension reason]}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product clears the suspension, republishes every address, and records the restoration in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: link, effect: changes, from: Suspended, to: Active, facts: [Suspension reason, Suspended by]}
  contexts:
    web:
      place: web::admin-console::all-links
---

# Restore a suspended link

## Trigger

An appeal succeeds or a suspension was a mistake.

## Outcome

The link redirects again on all its addresses.
