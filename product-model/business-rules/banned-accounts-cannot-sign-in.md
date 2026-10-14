---
appliesTo:
- type: entity
  id: account
  effect: changes
  to: Banned
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
- kind: code
  role: implementation
  target: src/worker/session.ts#withSession
---

# A banned account cannot sign in or act through keys or agents

Banning ends every session at once and refuses new ones; its API keys and connected apps are refused too. Its organizations and their links keep working.
