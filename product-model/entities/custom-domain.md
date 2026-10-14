---
domain: domains
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#domains
- kind: code
  role: implementation
  target: src/worker/routes/domains.ts#domainRoutes
---

# Custom domain

A hostname the organization owns, connected so its short links live there instead of on the shared domain. Slugs on a custom domain belong to that domain alone.

## Information kept

- **Hostname** — the bare hostname, such as links.example.com
- **Status reason** — why setup failed, shown while the domain is in Error
- **Root redirect** — where the domain's root, and any address on it that matches no link, sends people; empty shows a not-found page
- **Locked** — whether the domain is beyond the plan's custom domain limit after a downgrade
- **Created** — when it was added

## States

### Checking DNS

Waiting to see the CNAME record resolve.

### Issuing TLS

DNS resolves; waiting for the certificate.

### Active

Serving short links.

### Error

Setup did not finish within a day; the domain has to be deleted and added again.
