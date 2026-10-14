---
appliesTo:
- type: entity
  id: link
  effect: creates
- type: entity
  id: anonymous-link
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/abuse.ts#assertNotShortener
---

# A destination cannot be another URL shortener

Pointing a short link at another shortener hides the real destination from the people clicking and from the security check, so known shortener hosts are refused on every create path.
