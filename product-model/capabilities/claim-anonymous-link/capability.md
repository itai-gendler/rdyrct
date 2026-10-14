---
availability:
- {place: 'web::workspace'}
references:
- kind: code
  role: implementation
  target: src/worker/routes/shorten.ts#claimAnonLink
- kind: code
  role: implementation
  target: src/app/lib/anon-links.ts#claimPendingLinks
- kind: code
  role: implementation
  target: src/app/routes/shell.tsx
---

# Keep a home-page short address after signing up

Short addresses a person made on the home page before having an account move into their organization the first time the app opens after they sign up, as ordinary links that keep their slug.
