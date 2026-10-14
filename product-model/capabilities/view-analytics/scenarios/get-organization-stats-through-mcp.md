---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent asks for an organization's click stats over a number of days
  kind: actor
  actor: ai-agent
  entities:
  - {entity: organization, effect: reads, facts: []}
  - {entity: click, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product returns total and recent clicks, the link count, top links and links that went quiet
  kind: product
  actor: ai-agent
  entities:
  - {entity: click, effect: reads, facts: [Time]}
  - {entity: link, effect: reads, facts: [Slug, Title]}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent reads the organization's stats

## Trigger

A person asks their AI agent how their links are doing.

## Outcome

The AI agent has the summary.
