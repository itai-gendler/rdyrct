---
domain: members
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#invites
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#inviteRoutes
---

# Invite

A single-use invitation to join an organization with a given Role, valid for seven days. An emailed invite is for one address; a copied invite link works for whoever opens it.

## Information kept

- **Role** — the Role the person gets on joining: Admin, Member or Viewer
- **Email** — the address the invite was sent to; empty for a copied invite link
- **Invite link** — the address that opens the invite
- **Created** — when it was created
- **Expires** — seven days after it was created
