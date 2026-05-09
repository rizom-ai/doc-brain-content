---
title: Plugin System
---
A major topic is the plugin architecture, which divides behavior into EntityPlugin, ServicePlugin, InterfacePlugin, and MessageInterfacePlugin families. Entity plugins define durable markdown-backed content types, service plugins add tools and integrations, and interface plugins provide transports such as MCP, Discord, A2A, and webserver routes. The docs explain lifecycle hooks, registration patterns, public authoring APIs, and the external plugin loading model from `brain.yaml`. They also stress stable boundaries and the use of public `@rizom/brain/*` exports for outside packages. This is one of the most detailed areas in the batch because it underpins extensibility throughout the system.
