---
entities:
- {entity: account, shows: [Name, Email, Email verified, Platform admin, Plan, Subscription plan, Subscription status, Cancels at period end, Comp plan, Comp reason, Comp granted by, Comp granted at, Joined, Last seen], collects: [Comp plan, Comp reason]}
entryPoints:
- web: /admin/users
references:
- kind: code
  role: implementation
  target: src/app/routes/admin/users.tsx
---

# Users

Every account on the instance: plan and billing standing, comp, organizations, when they joined and were last seen, and the actions on each.
