---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: src/worker/routes/billing.ts#handlePolarWebhook
- kind: doc
  role: context
  target: README.md
  title: Selling plans
---

# Billing provider

The merchant of record that sells the Hobby and Pro plans (Polar). It runs checkout and the subscription portal, and tells the Product about every subscription change.
