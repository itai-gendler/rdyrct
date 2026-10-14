---
availability:
- {place: 'web::admin-console'}
domain: platform-links
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#setSuspended
- kind: code
  role: implementation
  target: src/worker/storage.ts#desiredLink
---

# Suspend link

Stop a link redirecting on every address it answers to, with a reason, while keeping it and its history so the decision can be reversed. Suspension holds through any later edit.
