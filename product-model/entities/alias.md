---
domain: links
references:
- kind: code
  role: implementation
  target: src/worker/db/schema.ts#linkAddresses
- kind: code
  role: implementation
  target: src/app/components/alias-thread.tsx
---

# Alias

An extra address of a link: another slug on the link's own domain that redirects to the same destination with the same UTM parameters. A rename leaves the old address behind as a temporary alias for 48 hours.

## Information kept

- **Slug** — the alias's path on the link's domain
- **Short URL** — the alias's full address
- **Origin** — how the alias began: added by hand, left by a rename, left by making another address primary, or added to an existing link with the same destination
- **Expires** — when a temporary alias stops redirecting, 48 hours after the rename
- **Created** — when it was created
- **Recent clicks** — clicks that came in on this alias over the last seven days
- **Last use** — the latest click on this alias
- **Top referrers** — where this alias's clicks came from over the last seven days

## States

### Permanent

The alias redirects until someone removes it, and counts toward the plan's link limit.

### Temporary

The alias redirects until it expires, and does not count toward the plan's link limit.

### Retired

The alias no longer redirects and its slug is free again; it stays for its click history.
