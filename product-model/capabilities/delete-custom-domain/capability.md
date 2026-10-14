---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
domain: domains
references:
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#domainRoutes
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#cfDeleteHostname
---

# Delete custom domain

Disconnect a custom domain. It cannot be deleted while any link or alias still uses it.
