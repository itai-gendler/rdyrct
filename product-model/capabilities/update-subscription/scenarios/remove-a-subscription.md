---
kind: alternative
routes:
  webhook: Billing webhook
steps:
- text: The Billing provider reports that a subscription was revoked
  kind: actor
  actor: billing-provider
  entities: []
  contexts:
    webhook:
      place: billing-webhook
- text: The Product drops the subscription, derives the person's plan, Free unless a comp remains, and applies it to the organizations they own
  kind: product
  actor: billing-provider
  entities:
  - {entity: account, effect: changes, facts: [Subscription plan, Subscription status, Cancels at period end, Period end, Plan]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    webhook:
      place: billing-webhook
---

# A subscription ends

## Trigger

The paid period ran out after a cancellation, or payment finally failed.

## Outcome

The person is on Free or their comp plan, and their organizations are checked against it.
