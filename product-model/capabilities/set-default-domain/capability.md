---
availability:
- {place: 'web::workspace'}
domain: domains
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#resolveDefaultDomain
- kind: code
  role: implementation
  target: src/app/routes/domains.tsx
---

# Set default domain

Make an active custom domain the one new links start on. A locked custom domain or one still setting up cannot be the default.
