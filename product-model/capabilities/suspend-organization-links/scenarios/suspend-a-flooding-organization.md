---
kind: primary
routes:
  web: Web app
steps:
- text: A recently created organization on the Free plan recorded more redirects today than the free plan's daily ceiling
  kind: condition
  unattended: true
  entities:
  - {entity: organization, effect: reads, facts: [Plan, Created]}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product suspends every active link of the organization with the reason, closes the organization to changes, and records it in the audit log
  kind: product
  entities:
  - {entity: organization, effect: changes, facts: [Links suspended]}
  - {entity: link, effect: changes, from: Active, to: Suspended, facts: [Suspension reason]}
  contexts:
    web:
      place: web::admin-console::all-links
- text: The Product emails the owner that the organization's links are suspended and why
  kind: product
  entities:
  - {entity: organization, effect: reads, facts: [Name]}
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::all-links
---

# Suspend a new free organization over the redirect ceiling

## Trigger

A brand-new free account starts driving heavy traffic through its links.

## Outcome

The organization's links answer not found and the organization takes no changes until a Platform admin lifts it.
