---
question: How is the Rizom ecosystem architected?
status: draft
asked: 6
---
# FAQ

## Answer
A brain is an independently deployable, MCP-first system composed of plugins and typed entities. Agent-to-agent communication is handled by a separate networking layer. Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

## Sources

- [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery "doc:agent-discovery")
- [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview "doc:architecture-overview")

## Alternative answers

### Alternative answer 1

#### Answer
A brain is a modular, independently deployable MCP server composed from plugins and configured bundles. Other brains connect through A2A agent networking, creating an ecosystem of composable brains and extensions with explicit peer approval and trust boundaries.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview), [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 2

#### Answer
A brain is an independently deployable MCP server composed of plugins and capability bundles. Typed entities hold durable content, while service and interface plugins add integrations and ways to connect. Other brains connect through an approval-gated agent network.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview), [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 3

#### Answer
A brain is an independently deployable MCP server, assembled from a definition, instance configuration, and plugins. Entity plugins provide durable content types, service plugins add tools and integrations, and interface plugins provide transports. **Sources:** [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Plugin System](https://docs.rizom.ai/docs/plugin-system).

### Alternative answer 4

#### Answer
Each brain runs as an independently deployable MCP server, assembled from a canonical definition and its `brain.yaml` configuration. The shell provides runtime services, while plugins add entity types, integrations, and interfaces. Brains can also connect to peer brains through the A2A interface.

Source: [Architecture Overview](/docs/architecture-overview).

### Alternative answer 5

#### Answer
The architecture favors **independent, modular brains**: each brain owns its identity and content, composes capabilities through plugins, and connects to peers through explicit discovery and approval—not open-ended automatic access.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview), [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).
