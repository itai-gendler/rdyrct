---
availability:
- {place: 'web::workspace'}
domain: settings
references:
- kind: code
  role: implementation
  target: src/worker/better-auth.ts#deleteAccountAndOwnedOrgs
- kind: code
  role: implementation
  target: src/app/routes/settings.tsx#SettingsPage
---

# Delete account

Delete the person's account together with every organization they own, teammates and all; organizations they only belong to are left alone. Settings names every owned organization before asking.
