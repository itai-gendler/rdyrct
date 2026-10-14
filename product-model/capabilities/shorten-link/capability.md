---
availability:
- {place: 'web::public'}
references:
- kind: code
  role: implementation
  target: src/worker/routes/shorten.ts#shortenRoutes
- kind: code
  role: implementation
  target: src/worker/routes/shorten.ts#sweepExpiredAnonLinks
- kind: code
  role: implementation
  target: src/worker/abuse.ts#assertNotShortener
- kind: code
  role: implementation
  target: src/app/components/hero-shortener.tsx
---

# Shorten a link without an account

Anyone on the home page can shorten a web address without an account. The result is an anonymous link on the shared domain that lasts 24 hours and counts only its total clicks; signing up keeps it.
