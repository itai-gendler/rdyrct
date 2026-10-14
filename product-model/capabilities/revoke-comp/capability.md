---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#writeComp
---

# Revoke comp

Take away a comped plan. The account falls back to its subscription, if one keeps access, or to Free.
