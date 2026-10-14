---
availability:
- {place: 'web::workspace'}
domain: domains
references:
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#domainRoutes
- kind: code
  role: implementation
  target: src/app/lib/domain-messages.ts
---

# Check domain status

See where a custom domain's setup stands. While it is checking, the page re-checks by itself every few seconds.
