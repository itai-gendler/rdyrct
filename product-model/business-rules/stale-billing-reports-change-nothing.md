---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Subscription status]
references:
- kind: code
  role: implementation
  target: src/worker/routes/billing.ts#handlePolarWebhook
---

# A subscription report older than the one recorded changes nothing

Each report carries when the subscription last changed at the billing provider, so a late or repeated delivery cannot undo a newer one.
