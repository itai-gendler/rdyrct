---
entities:
- {entity: account, shows: [Plan, Joined, Last seen]}
- {entity: organization, shows: [Over plan]}
entryPoints:
- web: /admin
references:
- kind: code
  role: implementation
  target: src/app/routes/admin/usage.tsx
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# Platform usage

Everything across all organizations: accounts, paid accounts and subscribers, sign-ups, weekly active users, organizations, links and clicks, the plan mix, an anomaly watchlist and organizations near their caps.
