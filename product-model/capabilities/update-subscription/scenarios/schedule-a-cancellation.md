---
kind: alternative
routes:
  webhook: Billing webhook
steps:
- text: The Billing provider reports that a subscription will cancel at the end of its period
  kind: actor
  actor: billing-provider
  entities: []
  contexts:
    webhook:
      place: billing-webhook
- text: The Product records that it cancels and when the period ends; paid access continues until then
  kind: product
  actor: billing-provider
  entities:
  - {entity: account, effect: changes, facts: [Cancels at period end, Period end]}
  contexts:
    webhook:
      place: billing-webhook
---

# A subscription is set to cancel

## Trigger

A subscriber cancelled in the portal.

## Outcome

Billing shows when the plan ends; nothing else changes yet.

## Edge cases

- A report that the cancellation was undone clears it again.
