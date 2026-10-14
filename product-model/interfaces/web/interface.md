---
type: web
actors:
- visitor
- user
- platform-admin
entryPoints:
- web: /
languages:
- en
references:
- kind: code
  role: implementation
  target: src/app/main.tsx
- kind: code
  role: implementation
  target: src/worker/index.ts
---

# Web app

The browser app at the instance's own host: the public pages where people shorten a link without an account, make QR codes, sign up and sign in; the workspace where members of an organization manage its links, custom domains, team and billing; and the admin console for Platform admins.
