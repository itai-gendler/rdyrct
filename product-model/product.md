---
id: rdyrct
summary: An organization-based link shortener with QR codes, custom domains, privacy-friendly click analytics and per-person plans.
category: link-shortener
tags:
- url-shortener
- qr-codes
- link-analytics
- custom-domains
- teams
authors:
- name: Andrea Bruno
  url: https://github.com/baronunread
license: MIT
languages:
- en
limitations:
- Links on the shared domain always get random slugs; choosing a slug needs a custom domain.
- 'Billing belongs to a person, not an organization: every organization works within its owner''s plan.'
- Clicks never keep an IP address; analytics show only country, referrer, device and time.
- Payments, tax and the subscription portal are left to the billing provider, and the Product reports plan counts, never revenue.
- 'A plan change never deletes anything: what no longer fits is locked, demoted or held in a grace period instead.'
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: context
  target: AGENTS.md
- kind: doc
  role: context
  target: docs/architecture.md
---

# rdyrct

rdyrct is a link shortener for teams. People work in organizations with owner, admin, member and viewer Roles; they create short links with random slugs on a shared domain or chosen slugs on their own custom domains, add aliases, style and download QR codes, and read click analytics that never store an IP address. Anyone can shorten a link for 24 hours without an account. Billing is per person through Free, Hobby and Pro plans, and a Platform admin runs the instance from an admin console with link moderation and an audit log. Members can also work through a REST API and connect an AI agent through an MCP server.

## Intent

In the project's own words, an "organization-based link shortener + QR codes, running entirely on Cloudflare's edge": short links with custom or random slugs and UTM parameters, renamed links that keep their old address for 48 hours, QR codes with a logo, custom domains, organizations with roles and magic-link invites, privacy-friendly analytics, and per-user plans. A downgrade never deletes: it locks and holds back what no longer fits, and an upgrade puts it back.
