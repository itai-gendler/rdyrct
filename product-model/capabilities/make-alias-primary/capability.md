---
availability:
- {place: 'web::workspace'}
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#promoteAddress
---

# Make alias primary

Make one of a link's aliases its primary address. The former primary address stays as a permanent alias.
