---
kind: edge
routes:
  webhook: Billing webhook
steps:
- text: The Billing provider delivers a report older than the subscription state the Product holds
  kind: actor
  actor: billing-provider
  entities: []
  contexts:
    webhook:
      place: billing-webhook
- text: The report is older than the last change recorded
  kind: condition
  actor: billing-provider
  entities:
  - {entity: account, effect: reads, facts: [Subscription status]}
  contexts:
    webhook:
      place: billing-webhook
- text: The Product acknowledges it and changes nothing
  kind: product
  actor: billing-provider
  entities: []
  contexts:
    webhook:
      place: billing-webhook
---

# Ignore an out-of-date report

## Trigger

Reports arrive late or twice.

## Outcome

The account reflects the newest report only.
