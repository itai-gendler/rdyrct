---
kind: alternative
routes:
  link: Short link
steps:
- text: The Visitor opens a custom domain's root, or a slug on it that matches no link
  kind: actor
  actor: visitor
  entities:
  - {entity: link, effect: reads, facts: []}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    link:
      place: short-links
- text: The Product redirects to the domain's root redirect, or shows not found when the domain has none
  kind: product
  actor: visitor
  entities:
  - {entity: custom-domain, effect: reads, facts: [Root redirect]}
  contexts:
    link:
      place: short-links
---

# Open a custom domain's root or an unknown slug on it

## Trigger

Someone types the bare branded domain.

## Outcome

The Visitor reaches the organization's chosen page or a not-found page.
