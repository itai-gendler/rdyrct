---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Name, Picture]
permits:
- related:
  - {verb: uses, entity: user}
references:
- kind: code
  role: implementation
  target: src/app/routes/settings.tsx#SettingsPage
---

# A person edits only their own name and picture

Nobody else changes a person's name or picture.
