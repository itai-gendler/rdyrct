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
  target: src/worker/workflows.ts#DomainActivateWorkflow
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#probeDomain
- kind: code
  role: implementation
  target: src/worker/plan.ts#insertDomainWithinLimit
---

# Add custom domain

Connect a hostname the organization owns. The Product sets it up in the background: it waits for the CNAME record to resolve, then for the certificate, and starts serving short links once both are ready, or gives up after a day. Custom domains need a paid plan.
