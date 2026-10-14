---
entities:
- {entity: organization, shows: [Name, Plan, Created]}
- {entity: membership, shows: [Role, Demoted]}
- {entity: account, shows: [Name, Email]}
- {entity: link, shows: [Short URL, Destination, Created, Clicks]}
entryPoints:
- web: /admin/orgs
references:
- kind: code
  role: implementation
  target: src/app/routes/admin/orgs.tsx
---

# Organizations

Every organization on the instance with its owner, plan, members, links and clicks, and one organization's members, links and last 30 days of clicks.
