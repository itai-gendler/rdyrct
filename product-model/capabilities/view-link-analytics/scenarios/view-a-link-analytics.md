---
kind: primary
routes:
  web: Web app
  api: REST API
steps:
- text: The User opens a link's analytics
  kind: actor
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL]}
  contexts:
    web:
      place: web::workspace::link-analytics
    api:
      place: rest-api
- text: The Product shows the link's destination, who made it and when, its clicks against the previous period, clicks per day, countries, referrers, devices and the latest click
  kind: product
  actor: user
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Destination, Title, Created, Created by]}
  - {entity: click, effect: reads, facts: [Time, Country, Referrer, Device]}
  contexts:
    web:
      place: web::workspace::link-analytics
    api:
      place: rest-api
---

# View one link's analytics

## Trigger

A member checks how one link performs.

## Outcome

The member sees the link's analytics.

## Edge cases

- Opening an alias's slug shows the analytics of the link it belongs to.
