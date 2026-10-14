---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent names a link by its slug or current destination and gives a new destination or title
  kind: actor
  actor: ai-agent
  entities:
  - {entity: link, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product finds the one matching link and saves the change exactly as the app would
  kind: product
  actor: ai-agent
  entities:
  - {entity: link, effect: changes, facts: [Destination, Title]}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent changes a link

## Trigger

A person asks their AI agent to point a link elsewhere.

## Outcome

The link redirects to the new destination.

## Edge cases

- When more than one link matches, the AI agent is asked to say which.
