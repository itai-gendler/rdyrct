---
entities:
- {entity: audit-entry, shows: [Who, Action, Target, Detail, When]}
entryPoints:
- web: /admin/audit
references:
- kind: code
  role: implementation
  target: src/app/routes/admin/audit.tsx
---

# Audit log

The audit log, newest first, searchable.
