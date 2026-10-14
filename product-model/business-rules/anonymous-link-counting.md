---
appliesTo:
- type: entity
  id: anonymous-link
  effect: changes
  facts: [Click total]
permits:
- actors:
  - visitor
references:
- kind: code
  role: implementation
  target: src/worker/clicks.ts#countAnonClick
---

# Following an anonymous short address only adds to its total

Whoever follows it adds one to its total; nothing else about it changes, and nothing about the visit is kept.
