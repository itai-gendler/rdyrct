---
entities:
- {entity: connected-app, shows: [App name, Scopes]}
entryPoints:
- web: /consent
references:
- kind: code
  role: implementation
  target: src/app/routes/consent.tsx
---

# Consent

Where a person decides whether an AI agent client may act for them: which client is asking and for what.
