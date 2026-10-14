---
availability:
- {place: 'web::public'}
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
- kind: code
  role: implementation
  target: src/app/lib/reset-password.ts
- kind: code
  role: implementation
  target: src/app/routes/reset-password.tsx
---

# Reset password

Ask for a password reset email from the sign-in page and choose a new password from it. Offered only where the instance sends email.
