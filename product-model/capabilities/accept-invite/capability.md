---
availability:
- {place: 'web::workspace'}
domain: members
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#inviteRoutes
- kind: code
  role: implementation
  target: src/worker/plan.ts#acceptInviteAtomically
- kind: code
  role: implementation
  target: src/app/routes/invite.tsx
---

# Accept invite

Join an organization from an invite. Someone not signed in is sent to sign in or sign up first and brought back. An emailed invite can only be accepted by the account with that address.
