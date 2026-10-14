---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent asks for the organization's links, optionally filtered
  kind: actor
  actor: ai-agent
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: link, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product returns the matching links with their click counts
  kind: product
  actor: ai-agent
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Destination, Title, Clicks]}
  - {entity: click, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent lists links

## Trigger

A person asks their AI agent which links they have.

## Outcome

The AI agent has the list.
