---
entities:
- {entity: invite, shows: [Role]}
- {entity: organization, shows: [Name]}
entryPoints:
- web: /invite/:token
references:
- kind: code
  role: implementation
  target: src/app/routes/invite.tsx
---

# Invite

The page an invite link opens: which organization and Role it offers, and accepting it.
