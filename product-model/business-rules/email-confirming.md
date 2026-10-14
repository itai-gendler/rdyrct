---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Email verified]
permits:
- actors:
  - visitor
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
---

# Only the holder of the emailed code confirms an address

The address is confirmed by entering the six-digit code sent to it, before or at the first sign-in; nobody confirms it for someone else.
