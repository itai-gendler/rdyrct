---
kind: alternative
routes:
  mcp: MCP server
steps:
- text: The AI agent asks for a link's stats by slug, with its custom domain if it has one
  kind: actor
  actor: ai-agent
  entities:
  - {entity: link, effect: reads, facts: []}
  - {entity: custom-domain, effect: reads, facts: []}
  contexts:
    mcp:
      place: mcp-server
- text: The Product returns the link's clicks, recent clicks, latest click, countries, referrers and devices
  kind: product
  actor: ai-agent
  entities:
  - {entity: link, effect: reads, facts: [Short URL, Destination, Title]}
  - {entity: click, effect: reads, facts: [Time, Country, Referrer, Device]}
  contexts:
    mcp:
      place: mcp-server
---

# An AI agent reads one link's stats

## Trigger

A person asks their AI agent where a link's clicks came from.

## Outcome

The AI agent has the link's numbers.
