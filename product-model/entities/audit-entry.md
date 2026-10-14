---
references:
- kind: code
  role: implementation
  target: src/worker/audit.ts#recordAdminAction
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#adminActions
---

# Audit entry

One line of the admin console's audit log: a moderation or account action a Platform admin, or the Product's own abuse control, took.

## Information kept

- **Who** — the Platform admin who acted, or the Product
- **Action** — what was done, such as suspending a link or banning an account
- **Target** — what it was done to
- **Detail** — what the entry needs to stay readable after its target is gone, such as the slug, destination, organization name or reason
- **When** — when it happened
