---
appliesTo:
- type: entity
  id: link
  effect: changes
  facts: [Risk score, Risk reasons, Risk checked]
references:
- kind: code
  role: implementation
  target: src/worker/risk.ts#scoreAndRecord
- kind: code
  role: implementation
  target: src/worker/risk.ts#revalidateOnRedirect
---

# The destination check scores and never refuses

A link's destination is checked after it is created or changed, and again after a redirect when the verdict is a day old; the check never stops a link being made or followed. A changed destination reads as unchecked until the new check lands.
