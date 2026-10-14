---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#validateIsAdminPatch
- kind: code
  role: implementation
  target: src/app/routes/admin/users.tsx
---

# Make platform admin

Give another account Platform admin rights.
