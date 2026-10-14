---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#validateIsAdminPatch
---

# Remove platform admin

Take Platform admin rights away from another account. A Platform admin cannot remove their own.
