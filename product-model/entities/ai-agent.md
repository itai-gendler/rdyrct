---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: src/worker/routes/mcp.ts#mcpRoutes
- kind: code
  role: implementation
  target: src/app/routes/docs.tsx#DocsPage
---

# AI agent

A person's own AI assistant or chatbot connector, calling the MCP server on their behalf. It signs in through the person's allowance (a connected app) or with one of their API keys, and can do only what that person may do.
