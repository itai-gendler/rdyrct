---
entities:
- {entity: custom-domain, shows: [Hostname, Status reason, Root redirect, Locked, Created], collects: [Hostname, Root redirect]}
- {entity: organization, shows: [Default domain, Grace period ends]}
entryPoints:
- web: /domains
references:
- kind: code
  role: implementation
  target: src/app/routes/domains.tsx
---

# Domains

The organization's custom domains, their setup status and DNS instructions, root redirects and which one new links default to.
