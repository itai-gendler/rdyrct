---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# Unban user

Lift a ban so the account can sign in again.
