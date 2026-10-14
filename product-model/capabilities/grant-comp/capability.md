---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#writeComp
- kind: code
  role: implementation
  target: src/app/routes/admin/comp-dialog.tsx
---

# Grant comp

Give an account a paid plan by hand, with a reason, or change the comped plan. A comp outranks any subscription and is never counted as a subscriber.
