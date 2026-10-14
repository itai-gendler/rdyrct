---
entities:
- {entity: account, collects: [Email]}
entryPoints:
- web: /login
references:
- kind: code
  role: implementation
  target: src/app/routes/auth.tsx#LoginPage
---

# Sign in

Signing in with an email and password, or with Google where offered, and asking for a password reset link.
