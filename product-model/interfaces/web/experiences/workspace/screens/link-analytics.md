---
entities:
- {entity: link, shows: [Short URL, Destination, Title, Created, Created by]}
- {entity: click, shows: [Time, Country, Referrer, Device]}
entryPoints:
- web: /links/:slug
references:
- kind: code
  role: implementation
  target: src/app/routes/link-detail.tsx
---

# Link analytics

One link's clicks over the plan's window: totals, clicks per day, countries, referrers, devices and the latest click.
