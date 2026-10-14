---
appliesTo:
- type: entity
  id: link
  effect: changes
  facts: [Suspension reason]
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin-links.ts#checkReason
---

# Suspending a link needs a reason

Restoring needs none.
