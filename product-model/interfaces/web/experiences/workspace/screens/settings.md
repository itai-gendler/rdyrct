---
entities:
- {entity: account, shows: [Name, Email, Picture], collects: [Name, Picture]}
- {entity: organization, shows: [Name]}
entryPoints:
- web: /settings
references:
- kind: code
  role: implementation
  target: src/app/routes/settings.tsx#SettingsPage
---

# Settings

The person's own account: name, picture, and deleting the account.
