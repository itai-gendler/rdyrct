---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin opens the admin console
  kind: actor
  actor: platform-admin
  entities: []
  contexts:
    web:
      place: web::admin-console::platform-usage
- text: The Product shows the instance's totals, trends, plan mix, anomaly watchlist and cap pressure
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Plan, Joined, Last seen]}
  - {entity: organization, effect: reads, facts: [Over plan]}
  contexts:
    web:
      place: web::admin-console::platform-usage
---

# View platform usage

## Trigger

A Platform admin checks on the instance.

## Outcome

The Platform admin sees how the instance is used.

## Edge cases

- When the instance has neither email nor Google sign-in, the console says accounts are not verified and passwords cannot be reset.
