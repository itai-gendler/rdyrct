---
availability:
- {place: 'web::workspace'}
domain: members
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#sweepExpiredInvites
- kind: code
  role: implementation
  target: src/app/routes/members.tsx
---

# Revoke invite

Withdraw a pending invite so it can no longer be used. Invites nobody used are removed once their seven days are over.
