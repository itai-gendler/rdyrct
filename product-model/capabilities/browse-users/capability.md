---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
- kind: code
  role: implementation
  target: src/app/routes/admin/users.tsx
---

# Browse users

See every account on the instance: plan and billing standing (paid, comped, past due, cancelling), comp, organizations, when they joined and were last seen, and addresses on disposable email domains.
