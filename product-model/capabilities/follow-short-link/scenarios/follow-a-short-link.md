---
kind: primary
routes:
  link: Short link
steps:
- text: The Visitor opens a short address on the shared domain
  kind: actor
  actor: visitor
  entities: []
  contexts:
    link:
      place: short-links
- text: The slug belongs to an active link that is not suspended
  kind: condition
  actor: visitor
  entities:
  - {entity: link, effect: reads, facts: [Slug, Destination, UTM parameters]}
  contexts:
    link:
      place: short-links
- text: The Product redirects to the destination with the UTM parameters added
  kind: product
  actor: visitor
  entities:
  - {entity: link, effect: reads, facts: [Destination, UTM parameters]}
  contexts:
    link:
      place: short-links
- text: After the redirect the Product records the click with its time, country, referrer, device and the address it came in on
  kind: product
  actor: visitor
  entities:
  - {entity: click, effect: creates, facts: [Time, Country, Referrer, Device, Address]}
  contexts:
    link:
      place: short-links
---

# Follow a short address

## Trigger

Someone follows a short link in a message, on a page or from a QR code.

## Outcome

The Visitor lands on the destination and the click appears in the organization's analytics.

## Edge cases

- A destination whose security check has gone stale is checked again after the redirect; the check never blocks it.
