---
title: Brain Architecture
---
The core structural design of a brain application, centered on a stable shared model, instance-level configuration in `brain.yaml`, and a lightweight runtime that turns the model into a running system. It emphasizes modular boundaries between core services and extension points so the architecture remains understandable, maintainable, and extensible as capabilities grow. A brain is also treated as an independently deployable MCP server with identity, content, capabilities, and interfaces, supporting reusable deployment across personal, team, and community contexts while preserving a clean separation of responsibilities.
