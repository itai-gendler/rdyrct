---
availability:
- {place: 'web::workspace'}
domain: domains
references:
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#domainRoutes
---

# Change domain root redirect

Choose where a custom domain's root, and any address on it that matches no link, sends people. Empty shows a not-found page.
