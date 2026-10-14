---
type: agent
actors:
- ai-agent
entryPoints:
- agent: /api/mcp
references:
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#mcpRoutes
- kind: code
  role: implementation
  target: src/worker/mcp-oauth.ts
- kind: code
  role: implementation
  target: src/app/routes/docs.tsx#DocsPage
---

# MCP server

A hosted MCP endpoint for a person's AI agent. The agent signs in through the person's own sign-in and consent, or with one of their API keys, and its tools do what the person's Role allows, within the organization's plan.
