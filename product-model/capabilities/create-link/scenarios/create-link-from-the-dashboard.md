---
kind: alternative
routes:
  web: Web app
steps:
- text: The User pastes a destination into the dashboard's quick create and picks a domain
  kind: actor
  actor: user
  entities:
  - {entity: organization, effect: reads, facts: [Default domain]}
  contexts:
    web:
      place: web::workspace::dashboard
- text: The Product creates the link with a random slug and shows it in the latest links
  kind: product
  actor: user
  entities:
  - {entity: link, effect: creates, to: Active, facts: [Slug, Domain, Short URL, Destination, Created by, Created, Clicks]}
  contexts:
    web:
      place: web::workspace::dashboard
---

# Shorten a link from the dashboard

## Trigger

A member shortens something quickly from the dashboard.

## Outcome

The link exists and redirects.
