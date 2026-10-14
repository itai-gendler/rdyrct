---
entities:
- {entity: click, shows: [Time, Country, Referrer, Device]}
- {entity: link, shows: [Slug, Title, UTM parameters]}
- {entity: organization, shows: [Plan]}
entryPoints:
- web: /analytics
references:
- kind: code
  role: implementation
  target: src/app/routes/analytics.tsx
---

# Analytics

The organization's clicks over the plan's window: totals against the previous period, clicks per day or per hour, top links, countries, referrers, devices, UTM campaigns, sources and mediums, a weekday-by-hour heatmap, links that went quiet and links whose clicks are falling.
