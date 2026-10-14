---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the dashboard
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::dashboard
- text: The Product shows the click totals, the latest clicks with country, referrer and device, and the latest links with who made them
  kind: product
  actor: user
  entities:
  - {entity: click, effect: reads, facts: [Time, Country, Referrer, Device]}
  - {entity: link, effect: reads, facts: [Short URL, Title, Created by, Created, Clicks]}
  contexts:
    web:
      place: web::workspace::dashboard
---

# Open the dashboard

## Trigger

A member checks in on the organization.

## Outcome

The member sees what happened lately.
