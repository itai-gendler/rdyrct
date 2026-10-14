---
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#clicks
- kind: code
  role: implementation
  target: src/worker/clicks.ts#enqueueClick
---

# Click

One time someone followed a link. The Product keeps where the visit came from in broad terms and never stores an IP address.

## Information kept

- **Time** — when the click happened
- **Country** — the visitor's country, or unknown
- **Referrer** — the referring site, or direct
- **Device** — desktop, mobile, tablet, bot or unknown
- **Address** — which address of the link it came in on: the primary address or an alias
