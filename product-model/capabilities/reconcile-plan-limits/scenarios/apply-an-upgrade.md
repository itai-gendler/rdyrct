---
kind: alternative
routes:
  web: Web app
steps:
- text: A person's plan went up
  kind: condition
  unattended: true
  entities:
  - {entity: account, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace
- text: The Product unlocks the owner's oldest locked organizations the plan now covers, gives demoted members back their Roles, unlocks custom domains, and clears the grace period
  kind: product
  entities:
  - {entity: organization, effect: changes, from: Locked, to: Active, facts: [Over plan, Grace period ends]}
  - {entity: membership, effect: changes, facts: [Role, Demoted]}
  - {entity: custom-domain, effect: changes, facts: [Locked]}
  contexts:
    web:
      place: web::workspace
---

# Apply an upgrade

## Trigger

A person subscribes to a higher plan or is granted a comp.

## Outcome

Everything locked or demoted by the earlier downgrade works again, with no re-verification of custom domains.
