---
kind: primary
routes:
  webhook: Billing webhook
steps:
- text: The Billing provider reports that a subscription for a person became active
  kind: actor
  actor: billing-provider
  entities: []
  contexts:
    webhook:
      place: billing-webhook
- text: The Product records the subscription's plan, status and customer, derives the person's plan, and applies it to the organizations they own
  kind: product
  actor: billing-provider
  entities:
  - {entity: account, effect: changes, facts: [Subscription plan, Subscription status, Billing account, Plan]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    webhook:
      place: billing-webhook
---

# A subscription starts

## Trigger

A person completed checkout.

## Outcome

The person has the paid plan and every organization they own works within it.
