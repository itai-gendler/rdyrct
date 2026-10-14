---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Manage subscription
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Billing account]}
  contexts:
    web:
      place: web::workspace::billing
- text: The person has a billing account
  kind: condition
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Billing account]}
  contexts:
    web:
      place: web::workspace::billing
- text: The Product opens the billing provider's portal for the person
  kind: product
  actor: user
  entities:
  - {entity: billing-provider, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::billing
---

# Open the subscription portal

## Trigger

A subscriber wants to change or cancel their plan.

## Outcome

The person is in the portal; whatever they change there arrives as a subscription update.
