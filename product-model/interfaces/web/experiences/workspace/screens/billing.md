---
entities:
- {entity: account, shows: [Plan, Subscription plan, Cancels at period end, Period end, Billing account, Comp plan]}
- {entity: organization, shows: [Over plan, Grace period ends]}
entryPoints:
- web: /billing
references:
- kind: code
  role: implementation
  target: src/app/routes/billing.tsx
---

# Billing

The person's plan, its usage against the plan's limits in the current organization, upgrading, and the subscription portal.
