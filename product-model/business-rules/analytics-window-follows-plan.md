---
appliesTo:
- type: entity
  id: click
  effect: reads
references:
- kind: code
  role: implementation
  target: src/worker/routes/orgs.ts#clampDays
---

# Analytics reach back only as far as the plan allows

Free sees 7 days, Hobby 30 and Pro 365; asking for more shows the plan's window.
