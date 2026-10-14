---
actors:
- user
references:
- kind: code
  role: implementation
  target: src/app/routes/invite.tsx
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#inviteRoutes
---

# Join an organization

## Goal

A person invited to a team joins its organization and starts working in it.

## Success criterion

The person is a member with the invite's Role and is looking at that organization's dashboard.
