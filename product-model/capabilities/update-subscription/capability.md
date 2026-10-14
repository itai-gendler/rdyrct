---
availability:
- {place: billing-webhook}
references:
- kind: code
  role: implementation
  target: src/worker/routes/billing.ts#handlePolarWebhook
- kind: code
  role: implementation
  target: src/worker/entitlement.ts#SUBSCRIPTION_ACCESS
- kind: code
  role: implementation
  target: src/worker/entitlement.ts#effectivePlanSql
- kind: doc
  role: context
  target: README.md
  title: Selling plans
---

# Update subscription

The billing provider reports a subscription starting, changing, being set to cancel, having the cancellation undone, or ending, and the Product records it on the person's account. Active, trialing and past-due subscriptions keep paid access; any other status keeps none. A report older than what the Product already holds changes nothing. Exists only on an instance that sells plans.
