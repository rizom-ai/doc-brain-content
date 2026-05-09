---
title: Brain Architecture
---
The core structure of the brain application and how a reusable brain model becomes a running system through instance-level configuration and a lightweight runtime shell. A brain is organized around clear separation between the shared model, deployment-specific configuration in `brain.yaml`, and the runtime that executes it. The architecture also frames brains as independently deployable MCP servers with identity, content, capabilities, and interfaces, making it a foundational concept for understanding the system’s internal design, extension points, and support for personal, team, and community deployments.
