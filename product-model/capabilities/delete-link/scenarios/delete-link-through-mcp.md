---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent names a link by its slug or destination and asks to delete it
  kind: actor
  actor: ai-agent
  entities:
  - {entity: link, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product finds the one matching link and deletes it as the app would
  kind: product
  actor: ai-agent
  entities:
  - {entity: link, effect: removes, from: Active}
  - {entity: click, effect: removes, with: link}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent deletes a link

## Trigger

A person asks their AI agent to remove a link.

## Outcome

The link is gone.
