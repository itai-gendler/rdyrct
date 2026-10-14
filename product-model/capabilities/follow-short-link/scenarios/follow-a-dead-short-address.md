---
kind: edge
routes:
  link: Short link
steps:
- text: The Visitor opens a short address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    link:
      place: short-links
- text: No active address has that slug, the link is suspended, the temporary alias or anonymous short address has expired, or the custom domain's grace period after a downgrade has ended
  kind: condition
  actor: visitor
  entities:
  - {entity: link, effect: reads, facts: [Slug]}
  - {entity: custom-domain, effect: reads, facts: [Locked]}
  - {entity: alias, effect: reads, facts: []}
  contexts:
    link:
      place: short-links
- text: The Product answers with a not-found page
  kind: product
  actor: visitor
  entities: []
  contexts:
    link:
      place: short-links
---

# A short address that does not redirect

## Trigger

Someone follows an address that no longer works or never existed.

## Outcome

The Visitor sees a not-found page and is not redirected.
