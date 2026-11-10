---
question: How is the Rizom ecosystem architected?
status: draft
asked: 25
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

### Alternative answer 6

#### Answer
The public docs describe an ecosystem of independently deployable brains, extended through focused plugins and connected through reviewed, trust-gated agent discovery and calls.

Sources: [Architecture Overview](/docs/architecture-overview) · [Agent Discovery](/docs/agent-discovery) · [Feature Overview](/docs/feature-overview)

### Alternative answer 7

#### Answer
The architecture describes independently deployable brains, extended through focused plugins and connected through reviewed agent relationships. It favors explicit composition and clear boundaries, while noting that the system is pre-stable and its APIs may change. This describes the public documentation, not a network consensus.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview), [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery), [Feature Overview](https://docs.rizom.ai/docs/feature-overview).

### Alternative answer 8

#### Answer
The ecosystem is built from independently deployable brains, modular plugins, and explicit capability bundles. Peers can connect through reviewed, approved agent discovery rather than open ambient discovery. This describes our public architecture, not a network consensus.

Sources: [Architecture Overview](/docs/architecture-overview), [Agent Discovery](/docs/agent-discovery).

### Alternative answer 9

#### Answer
The architecture favors independently deployable brains composed of focused plugins with clear public APIs. Brains can connect through reviewed, permission-gated agent networking. Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 10

#### Answer
The architecture is modular: independent brains compose typed plugins around an MCP-first core, and cross-brain discovery is gated—finding a peer doesn’t automatically grant access. Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 11

#### Answer
The ecosystem consists of independently deployable brains, extended through modular plugins and connected through reviewed, permissioned agent links—not an open, automatic mesh. Sources: [Architecture Overview](/docs/architecture-overview), [Agent Discovery](/docs/agent-discovery).

### Alternative answer 12

#### Answer
The ecosystem is built from independently deployable brains and composable plugins, with public APIs for extensions. For cross-brain collaboration, discovery is separate from permission: peers must be approved before they can be called.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview), [Plugin System](https://docs.rizom.ai/docs/plugin-system), [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 13

#### Answer
The public docs describe a modular-composition approach: brains combine focused plugins and capability bundles while remaining independently deployable. Peer discovery and calling are approval-gated, and ambient discovery is disabled. Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 14

#### Answer
The public docs describe an ecosystem of independently deployable brains built from modular plugins and explicit bundles, with standard interfaces for sharing capabilities and connecting peers. **Sources:** [Architecture Overview](/docs/architecture-overview) and [Agent Discovery](/docs/agent-discovery).

### Alternative answer 15

#### Answer
The ecosystem consists of independent, composable brains. Plugins add capabilities, while MCP and A2A provide ways to interact and connect. Cross-brain discovery is approval-gated rather than ambient.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) · [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery)

### Alternative answer 16

#### Answer
Rizom’s public documentation describes an ecosystem of independently deployable brains composed through plugins and bundles, with shared MCP and agent-to-agent connections. See [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 17

#### Answer
Our public docs favor **independent, composable brains**: each brain is deployable on its own, capabilities are added through plugins, and peers are connected through governed agent discovery. This describes our docs, not a network consensus.

Sources: [Architecture Overview](/docs/architecture-overview) and [Agent Discovery](/docs/agent-discovery).

### Alternative answer 18

#### Answer
Our public docs describe ecosystem architecture as **modular and interoperable**: independent brains expose capabilities through shared interfaces, while plugins and explicit bundles let each brain extend or configure itself without coupling everything together.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Feature Overview](https://docs.rizom.ai/docs/feature-overview).

### Alternative answer 19

#### Answer
The public docs describe an ecosystem of independently deployable brains, extended through plugins and connected to peers through reviewed, approved agent relationships. This is not a network consensus.

Sources: [Architecture Overview](/docs/architecture-overview), [Agent Discovery](/docs/agent-discovery).

### Alternative answer 20

#### Answer
The ecosystem is built from independently deployable brains, composed through plugins and capability bundles, with explicit approval governing peer connections. This favors modularity and controlled interoperability over a single shared system.

Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Agent Discovery](https://docs.rizom.ai/docs/agent-discovery).

### Alternative answer 21

#### Answer
The ecosystem is designed as independently deployable, plugin-composed brains, with shared interfaces and controlled peer discovery rather than one central runtime. See [Architecture Overview](/docs/architecture-overview) and [Agent Discovery](/docs/agent-discovery).

### Alternative answer 22

#### Answer
The public docs describe an ecosystem built from independent, deployable brains with explicit bundles and plugins, connected through interfaces such as MCP and A2A. This favors composability and clear boundaries over one central system.

Sources: [Architecture Overview](/docs/architecture-overview) and [Feature Overview](/docs/feature-overview).

### Alternative answer 23

#### Answer
The ecosystem consists of independently deployable brains connected through shared protocols, with plugins to extend capabilities and approval controls for peer calls. See [Architecture Overview](/docs/architecture-overview) and [Agent Discovery](/docs/agent-discovery).

### Alternative answer 24

#### Answer
The architectural theme is modularity: brains are independently deployable, plugin-composed systems, while MCP and agent discovery let them connect across a network. Sources: [Architecture Overview](https://docs.rizom.ai/docs/architecture-overview) and [Feature Overview](https://docs.rizom.ai/docs/feature-overview).
