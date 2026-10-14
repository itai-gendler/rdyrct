---
appliesTo:
- type: entity
  id: link
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#findSameDestinationLinks
---

# One destination with the same UTM parameters is one link per domain

Creating a link whose destination and UTM parameters match an existing link of the organization on the same domain first offers to add the address to that link, so its settings and analytics stay together. A different UTM value is a different link.
