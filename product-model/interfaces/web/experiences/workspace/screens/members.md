---
entities:
- {entity: membership, shows: [Role, Demoted, Joined], collects: [Role]}
- {entity: account, shows: [Name, Email]}
- {entity: invite, shows: [Role, Email, Invite link, Expires], collects: [Role, Email]}
entryPoints:
- web: /members
references:
- kind: code
  role: implementation
  target: src/app/routes/members.tsx
---

# Members

Who belongs to the organization and with which Role, the pending invites, and how many seats the plan leaves.
