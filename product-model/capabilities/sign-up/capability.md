---
availability:
- {place: 'web::public'}
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
- kind: code
  role: implementation
  target: src/app/routes/auth.tsx#SignupPage
- kind: code
  role: implementation
  target: src/shared/org-name.ts
---

# Sign up

Create an account with an email address and password, or continue with Google where the instance offers it. Where the instance sends email, the address is confirmed with a six-digit code before the first sign-in. Every account owns an organization from its first session, named from its email domain.
