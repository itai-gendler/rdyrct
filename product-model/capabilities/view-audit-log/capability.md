---
availability:
- {place: 'web::admin-console'}
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
- kind: code
  role: implementation
  target: src/app/routes/admin/audit.tsx
---

# View audit log

Read the audit log of moderation and account actions, newest first, optionally for one target.
