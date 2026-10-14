---
domain: members
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#orgMembers
- kind: code
  role: implementation
  target: src/worker/org-role.ts#requireOrgRole
---

# Membership

A person's place in one organization and the Role they hold there.

## Information kept

- **Role** — Owner, Admin, Member or Viewer. Owner is the one person the organization belongs to; Admin manages links and the team; Member manages links; Viewer reads only
- **Demoted** — the Role the person held before a downgrade made them a Viewer; empty when they hold the Role they were given
- **Joined** — when the person joined
