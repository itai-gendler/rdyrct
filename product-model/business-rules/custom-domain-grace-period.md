---
appliesTo:
- type: entity
  id: custom-domain
  effect: changes
  facts: [Locked]
references:
- kind: code
  role: implementation
  target: src/shared/types.ts#GRACE_PERIOD_MS
- kind: code
  role: implementation
  target: src/worker/storage.ts#desiredLink
- kind: code
  role: implementation
  target: src/worker/kv.ts#domainServing
---

# Custom domains beyond the plan keep serving for 30 days

After a downgrade, custom domains beyond the plan keep redirecting for a 30-day grace period and then stop. The owner is emailed when it starts and a week before it ends. An upgrade brings them back with no new DNS setup.
