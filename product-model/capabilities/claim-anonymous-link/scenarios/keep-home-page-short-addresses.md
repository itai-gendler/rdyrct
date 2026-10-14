---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the app for the first time after signing up
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::dashboard
- text: The browser holds short addresses the person made on the home page, and they have an organization
  kind: condition
  actor: user
  entities:
  - {entity: anonymous-link, effect: reads, facts: [Expires]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::dashboard
- text: The Product moves each one still within its 24 hours into the organization as a link with the same slug and destination
  kind: product
  actor: user
  entities:
  - {entity: anonymous-link, effect: removes}
  - {entity: link, effect: creates, to: Active, facts: [Slug, Domain, Short URL, Destination, Created by, Created, Risk score]}
  - {entity: organization, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::dashboard
- text: The Product says how many were kept
  kind: product
  actor: user
  entities:
  - {entity: link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::dashboard
---

# Keep short addresses made before signing up

## Trigger

A person who shortened something on the home page signs up.

## Outcome

Those addresses keep redirecting as the organization's links, now with full analytics.

## Edge cases

- One that expired, was already kept, or does not fit the plan's link limit is skipped without a message.
