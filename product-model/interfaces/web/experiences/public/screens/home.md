---
entities:
- {entity: anonymous-link, shows: [Slug, Destination, Expires, Click total], collects: [Destination]}
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: src/app/components/hero-shortener.tsx
---

# Home

The landing page, with a shortener anyone can use without an account and the link it made, its click total and when it expires.
