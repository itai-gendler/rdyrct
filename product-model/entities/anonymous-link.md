---
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#anonLinks
- kind: code
  role: implementation
  target: src/worker/routes/shorten.ts#shortenRoutes
---

# Anonymous link

A short link made on the home page by someone with no account. It lives 24 hours on the shared domain and counts only its total clicks, unless the person who made it signs up and it moves into their organization.

## Information kept

- **Slug** — its random path on the shared domain
- **Destination** — where it sends people
- **Expires** — 24 hours after it was made
- **Click total** — how many times it was followed; nothing else about the clicks is kept
- **Risk score** — the destination's risk, as for links
