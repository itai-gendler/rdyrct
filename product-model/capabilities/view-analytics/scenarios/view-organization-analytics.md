---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User opens analytics and picks a window or the last 24 hours by hour
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Plan]}
  contexts:
    web:
      place: web::workspace::analytics
    api:
      place: rest-api
- text: The Product shows totals against the previous period, clicks over time, top links, countries, referrers, devices, UTM campaigns, sources and mediums, a weekday-by-hour heatmap, links with no clicks in 30 days and links whose clicks halved
  kind: product
  actor: user
  entities:
  - {entity: click, effect: reads, facts: [Time, Country, Referrer, Device]}
  - {entity: link, effect: reads, facts: [Slug, Title, UTM parameters]}
  contexts:
    web:
      place: web::workspace::analytics
    api:
      place: rest-api
---

# View the organization's analytics

## Trigger

A member wants to know how the organization's links perform.

## Outcome

The member sees the organization's click analytics within the plan's window.

## Edge cases

- A window longer than the plan allows is cut to the plan's window.
- The member can export what is on screen as CSV.
