---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# Delete user

Delete an account from the admin console. An account that owns organizations cannot be deleted this way until those organizations are deleted; links it made stay with their organizations.
