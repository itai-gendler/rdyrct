---
kind: primary
routes:
  web: Web app
steps:
- text: The Platform admin opens Users, searching or sorting the list
  kind: actor
  actor: platform-admin
  entities:
  - {entity: user, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
- text: The Product lists every account with its plan, subscription standing, comp, organization count, joining date and last activity
  kind: product
  actor: platform-admin
  entities:
  - {entity: account, effect: reads, facts: [Name, Email, Email verified, Platform admin, Plan, Subscription plan, Subscription status, Cancels at period end, Comp plan, Comp reason, Comp granted by, Comp granted at, Joined, Last seen]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::admin-console::users
---

# Browse accounts

## Trigger

A Platform admin looks someone up.

## Outcome

The Platform admin sees the account's standing.
