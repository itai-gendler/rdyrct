---
availability:
- {place: 'web::admin-console'}
domain: platform-users
references:
- kind: code
  role: implementation
  target: src/worker/routes/admin.ts#validateBannedPatch
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
---

# Ban user

Ban an account: its sessions end at once and it cannot sign in, while its organizations and their links keep working. Another Platform admin cannot be banned, nor can oneself.
