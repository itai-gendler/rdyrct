---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Plan]
references:
- kind: code
  role: implementation
  target: src/worker/entitlement.ts#resolveEffectivePlan
- kind: code
  role: implementation
  target: src/worker/entitlement.ts#SUBSCRIPTION_ACCESS
---

# A person's plan is the comp first, then a subscription that keeps access, then Free

A comp outranks the subscription underneath it, so a subscription ending cannot take away access a Platform admin gave. A subscription keeps paid access while it is active, trialing or past due; canceled, unpaid, incomplete and any status the Product does not know keep none.
