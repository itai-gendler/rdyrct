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

# Open subscription portal

Open the billing provider's subscription portal to switch plans, update payment or cancel. Changes made there reach the Product as subscription updates. A comped plan with no billing account has no portal.
