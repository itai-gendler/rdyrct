---
entities:
- {entity: account, collects: [Email]}
entryPoints:
- web: /signup
references:
- kind: code
  role: implementation
  target: src/app/routes/auth.tsx#SignupPage
---

# Sign up

Creating an account with an email and password, or with Google where the instance offers it, and entering the emailed code.
