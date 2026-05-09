---
title: Plugin System
---
A plugin system is a modular extension architecture that lets an application gain new capabilities without changing its core code. It provides stable extension points for discovering, loading, registering, and integrating plugins while keeping a clear boundary between core logic and add-on functionality. A well-designed plugin system supports separation of concerns, long-term maintainability, compatibility, and safety as the platform evolves.

In this application, the plugin system is the main extensibility mechanism. It includes distinct plugin families: entity plugins define durable markdown-backed content types, service plugins add tools and integrations, and interface plugins expose transports and routes such as MCP, Discord, A2A, and webserver endpoints. Related concerns include lifecycle hooks, authoring and registration patterns, external plugin loading through `brain.yaml`, and public `@rizom/brain/*` exports for third-party packages.
