---
relations:
- {entity: alias, verb: has, cardinality: one-to-many}
- {entity: click, verb: has, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#links
- kind: code
  role: implementation
  target: src/worker/routes/links.ts#linkRoutes
- kind: code
  role: implementation
  target: src/shared/types.ts#LinkDTO
---

# Link

A short link that sends whoever follows it to a destination. Every link has one primary address (its slug on its domain) and may carry aliases that answer the same way.

## Information kept

- **Slug** — the path of the primary address; random on the shared domain, chosen or random on a custom domain
- **Domain** — the custom domain the link lives on, or the shared domain; fixed once the link exists
- **Short URL** — the full primary address
- **Destination** — the web address the link sends people to, kept without UTM parameters
- **Title** — an optional label
- **UTM parameters** — source, medium, campaign, term and content, added to the destination at redirect time
- **QR style** — the logo, pattern, colors, corner style, background, eye color and logo size of this link's QR code, over the organization's QR defaults
- **Created by** — who created the link
- **Created** — when it was created
- **Clicks** — how many clicks the link has recorded
- **Risk score** — 0 when nothing is known against the destination, 100 when a security resolver refuses to resolve it; empty until checked
- **Risk reasons** — why the destination scored as it did
- **Risk checked** — when the destination was last checked
- **Suspension reason** — why the link was suspended
- **Suspended by** — the Platform admin who suspended it; empty when the Product suspended it on its own

## States

### Active

The link redirects on every address it answers to.

### Suspended

The link no longer redirects on any of its addresses, whatever is later edited.
