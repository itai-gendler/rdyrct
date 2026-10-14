---
appliesTo:
- type: entity
  id: link
  effect: reads
  facts: [Risk score, Risk reasons, Risk checked]
- type: entity
  id: anonymous-link
  effect: reads
  facts: [Risk score]
permits:
- actors:
  - platform-admin
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#links
- kind: code
  role: implementation
  target: src/worker/risk.ts#scoreDestination
---

# Only platform admins see a destination's risk

The risk score, its reasons and when it was checked are for moderation and never appear in an organization's own views.
