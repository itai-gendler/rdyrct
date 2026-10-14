---
type: webhook
actors:
- billing-provider
entryPoints:
- webhook: /api/webhooks/polar
references:
- kind: code
  role: implementation
  target: src/worker/routes/billing.ts#handlePolarWebhook
---

# Billing webhook

Where the billing provider reports subscription changes. Exists only on an instance that sells plans.
