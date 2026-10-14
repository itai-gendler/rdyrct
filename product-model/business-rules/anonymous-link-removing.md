---
appliesTo:
- type: entity
  id: anonymous-link
  effect: removes
permits:
- actors:
  - user
- actors:
  - platform-admin
- unattended: true
references:
- kind: code
  role: implementation
  target: src/worker/routes/shorten.ts#claimAnonLink
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#adminLinkRoutes
---

# Anonymous short addresses go by expiry, by being kept, or by a platform admin

The browser that made a short address on the home page keeps it by signing up; otherwise it expires, unless a Platform admin deletes it first.
