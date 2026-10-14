---
availability:
- {place: 'web::workspace'}
domain: billing
references:
- kind: code
  role: implementation
  target: src/worker/routes/billing.ts#billingRoutes
- kind: code
  role: implementation
  target: src/app/routes/billing.tsx
---

# Upgrade plan

Buy the Hobby or Pro plan through the billing provider's checkout. Billing belongs to the person, not the organization, and works even before they have one. Exists only on an instance that sells plans.
