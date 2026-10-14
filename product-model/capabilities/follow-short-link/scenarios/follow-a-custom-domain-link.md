---
kind: alternative
routes:
  link: Short link
steps:
- text: The Visitor opens a short address on an organization's custom domain
  kind: actor
  actor: visitor
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    link:
      place: short-links
- text: The custom domain is active and still serving
  kind: condition
  actor: visitor
  entities:
  - {entity: custom-domain, effect: reads, facts: [Hostname, Locked]}
  contexts:
    link:
      place: short-links
- text: The Product redirects to the link's destination and records the click
  kind: product
  actor: visitor
  entities:
  - {entity: link, effect: reads, facts: [Destination, UTM parameters]}
  - {entity: click, effect: creates, facts: [Time, Country, Referrer, Device, Address]}
  contexts:
    link:
      place: short-links
---

# Follow a short address on a custom domain

## Trigger

Someone follows a branded short link.

## Outcome

The Visitor lands on the destination.
