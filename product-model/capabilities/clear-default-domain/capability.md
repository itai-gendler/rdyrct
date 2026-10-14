---
availability:
- {place: 'web::workspace'}
domain: domains
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#resolveDefaultDomain
---

# Clear default domain

Stop defaulting new links to a custom domain, so they start on the shared domain again.
