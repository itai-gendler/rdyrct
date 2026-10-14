---
appliesTo:
- type: entity
  id: alias
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#assertAliasQuota
---

# A link holds at most five aliases

Temporary and permanent aliases count together; the primary address does not.
