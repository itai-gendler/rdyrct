---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin chooses Suspend link and gives a reason
  kind: actor
  actor: platform-admin
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Destination]}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product suspends the link, stops every one of its addresses redirecting, and records the suspension with slug, organization, destination and reason in the audit log
  kind: product
  actor: platform-admin
  entities:
  - {entity: link, effect: changes, from: Active, to: Suspended, facts: [Suspension reason, Suspended by]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::all-links
---

# Suspend a link

## Trigger

A reported link points at phishing or malware.

## Outcome

Every address of the link answers not found; the members still see the link in their workspace.

## Edge cases

- Suspending without a reason is refused.
