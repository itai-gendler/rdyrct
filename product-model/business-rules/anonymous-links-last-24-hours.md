---
appliesTo:
- type: entity
  id: anonymous-link
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/routes/shorten.ts#shortenRoutes
---

# A home-page short address lasts 24 hours unless it is kept

It counts its total clicks only. Signing up within the 24 hours moves it into the person's organization with full analytics.
