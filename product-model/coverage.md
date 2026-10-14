---
scope: The rdyrct Worker, its shared types and its React app at the pinned commit.
method: Static inspection of source, migrations and project documentation; nothing was run.
covered:
- description: Worker entry, redirect path, publishing and scheduled sweeps
  paths:
  - src/worker/index.ts
  - src/worker/kv.ts
  - src/worker/storage.ts
  - src/worker/clicks.ts
  - src/worker/click-buffer.ts
  - src/worker/workflows.ts
  - src/worker/util.ts
  - src/worker/links-page.ts
- description: Worker API routes
  paths:
  - src/worker/routes/
- description: Plans, plan-change reconciliation and entitlement
  paths:
  - src/worker/plan.ts
  - src/worker/reconcile.ts
  - src/worker/entitlement.ts
  - src/worker/billing-provider.ts
- description: Authentication, sessions, organization roles, API keys and MCP sign-in
  paths:
  - src/worker/better-auth.ts
  - src/worker/session.ts
  - src/worker/org-role.ts
  - src/worker/guards.ts
  - src/worker/api-keys.ts
  - src/worker/mcp-oauth.ts
  - src/worker/password.ts
- description: Abuse controls, destination risk scoring and the admin audit log
  paths:
  - src/worker/abuse.ts
  - src/worker/risk.ts
  - src/worker/audit.ts
- description: Transactional email sending and content
  paths:
  - src/worker/email.ts
  - src/worker/email-layout.ts
  - src/worker/email-html.ts
- description: Database schema and migrations
  paths:
  - src/worker/db/
  - migrations/
- description: Shared types, plan limits and organization naming
  paths:
  - src/shared/types.ts
  - src/shared/org-name.ts
- description: App pages for the workspace, the admin console, sign-in and the public tools
  paths:
  - src/app/main.tsx
  - src/app/routes/admin/
  - src/app/routes/analytics.tsx
  - src/app/routes/api-keys.tsx
  - src/app/routes/auth.tsx
  - src/app/routes/billing.tsx
  - src/app/routes/consent.tsx
  - src/app/routes/dashboard.tsx
  - src/app/routes/dashboard-view.ts
  - src/app/routes/domains.tsx
  - src/app/routes/invite.tsx
  - src/app/routes/link-detail.tsx
  - src/app/routes/links.tsx
  - src/app/routes/members.tsx
  - src/app/routes/organization.tsx
  - src/app/routes/qr-generator.tsx
  - src/app/routes/reset-password.tsx
  - src/app/routes/settings.tsx
  - src/app/routes/shell.tsx
- description: App feature components and client logic behind those pages
  paths:
  - src/app/components/alias-thread.tsx
  - src/app/components/anon-link-bar.tsx
  - src/app/components/auth-form.tsx
  - src/app/components/avatar-input.tsx
  - src/app/components/avatar-picture-dialog.tsx
  - src/app/components/create-alias-dialog.tsx
  - src/app/components/hero-shortener.tsx
  - src/app/components/link-editor.tsx
  - src/app/components/links-table.tsx
  - src/app/components/member-dialogs.tsx
  - src/app/components/no-org.tsx
  - src/app/components/over-limit.tsx
  - src/app/components/qr-defaults-card.tsx
  - src/app/components/qr-fields.tsx
  - src/app/components/qr-logo-input.tsx
  - src/app/components/qr.tsx
  - src/app/components/same-destination-dialog.tsx
  - src/app/components/mcp-connect-wizard.tsx
  - src/app/lib/anon-links.ts
  - src/app/lib/api.ts
  - src/app/lib/auth-client.ts
  - src/app/lib/current-org.ts
  - src/app/lib/default-domain.ts
  - src/app/lib/domain-messages.ts
  - src/app/lib/grace.ts
  - src/app/lib/hooks.ts
  - src/app/lib/org-limits.ts
  - src/app/lib/org-qr.ts
  - src/app/lib/reset-password.ts
  - src/app/lib/shorten-anon.ts
  - src/app/lib/billing-page.ts
  - src/app/lib/plan-status-notes.ts
exclusions:
- description: UI kit, styles, icons, charts and static assets
  paths:
  - src/app/ui/
  - src/app/styles.css
  - src/app/assets/
  - src/app/data/
  - public/
  - index.html
  - src/app/components/charts.tsx
  - src/app/components/chart-tooltip.ts
  - src/app/components/country-map.tsx
  - src/app/components/skeletons.tsx
  - src/app/components/user-avatar.tsx
- description: 'Request plumbing: rate limits, body limits, security headers, bot check, logging and error reporting'
  paths:
  - src/worker/rate-limit.ts
  - src/worker/body-limit.ts
  - src/worker/security-headers.ts
  - src/worker/cap.ts
  - src/worker/cap-unused-dep-stub.ts
  - src/worker/evlog.ts
  - src/worker/sentry.ts
  - src/worker/background.ts
  - src/worker/schemas.ts
  - src/worker/env.ts
  - src/shared/lookup.ts
  - src/app/lib/sentry.ts
  - src/app/lib/cap.ts
  - src/app/lib/cap-retry.ts
  - evlog.map.json
- description: Marketing, pricing, roadmap, legal and developer documentation pages and their page metadata
  paths:
  - src/app/routes/landing.tsx
  - src/app/routes/pricing.tsx
  - src/app/routes/roadmap.tsx
  - src/app/routes/privacy.tsx
  - src/app/routes/terms.tsx
  - src/app/routes/docs.tsx
  - src/app/routes/not-found.tsx
  - src/worker/page-meta.ts
  - src/worker/not-found-page.ts
  - src/shared/page-meta.ts
  - src/app/components/landing-analytics.tsx
  - src/app/components/landing-header.tsx
  - src/app/components/landing-tour.tsx
  - src/app/components/legal-page-layout.tsx
  - src/app/components/marketing-glow.tsx
  - src/app/components/marketing-link.tsx
  - src/app/components/marketing-page.tsx
  - src/app/components/faq-json-ld.tsx
  - src/app/components/hero-signed-in.tsx
  - src/app/lib/landing-mock-data.ts
  - src/app/lib/seo.ts
  - src/app/lib/plan-finder.ts
  - src/app/lib/marketing-scroll.ts
- description: Product analytics, consent banner, experiments and click tracking of the site itself
  paths:
  - src/app/lib/posthog.ts
  - src/app/lib/consent.ts
  - src/app/lib/consent-buffer.ts
  - src/app/lib/funnel.ts
  - src/app/lib/track-cta.ts
  - src/app/lib/hero-variant.ts
  - src/app/lib/audience.ts
  - src/app/lib/last-auth.ts
- description: Tests, CI, local scripts, tooling configuration and agent skills
  paths:
  - tests/
  - scripts/
  - .github/
  - .oxlint/
  - .claude/
  - .agents/
  - .pi/
  - .codegraph/
  - .vscode/
  - fallow-baselines/
  - package.json
  - bun.lock
  - tsconfig.json
  - tsconfig.worker.json
  - vitest.config.ts
  - playwright.config.ts
  - lefthook.yml
  - .oxlintrc.json
  - .oxfmtrc.json
  - .fallowrc.jsonc
  - doctor.config.json
  - .coderabbit.yaml
  - .style-doctor.json
  - skills-lock.json
  - google.emulate.yaml
- description: Deployment and environment configuration
  paths:
  - wrangler.jsonc
  - vite.config.ts
  - drizzle.config.ts
  - .dev.vars.example
  - .dev.vars.playwright
  - .env.example
  - prod.secrets.env.example
- description: 'Client conveniences with no product meaning: theme, caching, clipboard, formatting and navigation helpers'
  paths:
  - src/app/lib/theme.ts
  - src/app/lib/user-cache.ts
  - src/app/lib/clipboard.ts
  - src/app/lib/numbers.ts
  - src/app/lib/dates.ts
  - src/app/lib/sort.ts
  - src/app/lib/use-debounced.ts
  - src/app/lib/use-shake.ts
  - src/app/lib/hydrated.ts
  - src/app/lib/router-search.tsx
  - src/app/lib/plain-click.ts
  - src/app/lib/new-version.ts
  - src/app/lib/last-seen.ts
  - src/app/lib/error-message.ts
  - src/app/lib/form-errors.ts
  - src/app/lib/mutation-toast.ts
  - src/app/lib/auth-errors.ts
  - src/app/lib/schemas.ts
  - src/app/lib/password-strength.ts
  - src/app/lib/link-display.ts
  - src/app/lib/click-buckets.ts
  - src/app/lib/qr-look.ts
  - src/app/lib/qr-seams.ts
  - src/app/lib/mcp-url.ts
  - src/app/components/error-boundary.tsx
  - src/app/components/new-version-banner.tsx
  - src/app/components/not-found-view.tsx
  - src/app/components/qr-color-field.tsx
  - src/app/components/link-preview-dialog.tsx
  - src/app/components/mcp-setup-prompt.tsx
  - src/app/components/nav-items.ts
  - src/app/components/command-menu.tsx
- description: Project documentation and licensing
  paths:
  - README.md
  - AGENTS.md
  - CLAUDE.md
  - CHANGELOG.md
  - LICENSE
  - THIRD_PARTY_LICENSES.md
  - docs/
  - .gitignore
unmapped:
- description: In-browser WebMCP tools that let an agent drive the open page
  paths:
  - src/app/components/webmcp-analytics-tool.tsx
  - src/app/components/webmcp-link-tools.tsx
  - src/app/components/webmcp-marketing-tools.tsx
  - src/app/lib/webmcp.ts
- description: CSV export of on-screen analytics
  paths:
  - src/app/components/export-csv-button.tsx
  - src/app/lib/csv.ts
- description: 'Admin routes no console page calls: whole-organization link suspension and its lifting, and a manual plan reconciliation run'
  paths:
  - src/worker/routes/admin-links.ts
  - src/worker/routes/admin.ts
limitations: []
---

# Coverage
