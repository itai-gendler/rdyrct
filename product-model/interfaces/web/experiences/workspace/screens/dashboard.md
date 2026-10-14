---
entities:
- {entity: link, shows: [Short URL, Destination, Title, Created by, Created, Clicks], collects: [Destination, Domain]}
- {entity: click, shows: [Time, Country, Referrer, Device]}
- {entity: organization, shows: [Default domain]}
entryPoints:
- web: /dashboard
references:
- kind: code
  role: implementation
  target: src/app/routes/dashboard.tsx
---

# Dashboard

The current organization at a glance: a quick way to shorten a link, the click totals, the latest clicks and the latest links.
