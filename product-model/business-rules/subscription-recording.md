---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Subscription plan, Subscription status, Cancels at period end, Period end, Billing account]
permits:
- actors:
  - billing-provider
references:
- kind: code
  role: implementation
  target: src/worker/routes/billing.ts#handlePolarWebhook
---

# Only the billing provider changes subscription facts

What a subscription is, its status and its cancellation come from the billing provider's reports alone; no person and no comp writes them.
