---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Re-check destination on a link
  kind: actor
  actor: platform-admin
  entities:
  - {entity: link, effect: reads, facts: [Destination, Risk score]}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product checks the destination's host with the security resolver, records the new score when it gets an answer, and records the check in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: link, effect: changes, facts: [Risk score, Risk reasons, Risk checked]}
  contexts:
    web:
      place: web::admin-console::all-links
---

# Re-check a link's destination

## Trigger

A Platform admin wants a fresh verdict on a reported destination.

## Outcome

The link shows the new risk score, or stays unscored if the resolver did not answer.
