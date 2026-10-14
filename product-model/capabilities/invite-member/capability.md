---
availability:
- {place: 'web::workspace'}
- {place: rest-api}
- {place: mcp-server}
domain: members
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#occupiedSeats
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#orgRoutes
- kind: code
  role: implementation
  target: src/app/components/member-dialogs.tsx
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#inviteMember
---

# Invite member

Invite people to the organization with a Role of Admin, Member or Viewer: by email, one invite per address, or as an invite link to copy and share. Every invite is single-use and lasts seven days, and open invites hold a seat against the plan's member limit.
