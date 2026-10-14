---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Comp reason]
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#adminRoutes
---

# A comp always carries a reason

Paid access nobody can account for later is what the reason prevents; it is at most 500 characters.
