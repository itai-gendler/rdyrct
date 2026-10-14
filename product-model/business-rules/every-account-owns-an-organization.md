---
appliesTo:
- type: entity
  id: organization
  effect: creates
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts
- kind: code
  role: implementation
  target: src/shared/org-name.ts
---

# Every new account owns an organization from its first session

Nobody meets an empty app behind a form; the organization is named from the email domain and can be renamed. A person who later deletes their last organization is offered to create one.
