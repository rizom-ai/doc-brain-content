---
title: Plugin System
---
A plugin system is a modular extension architecture that lets external or optional capabilities integrate into an application without changing its core logic. It defines stable extension points and clear contracts for discovering, loading, registering, and invoking plugins, preserving separation between the core system and add-on functionality.

A well-designed plugin system keeps the base application lightweight while enabling controlled growth through optional features, specialized behaviors, and third-party integrations. It should fit naturally into the core architecture rather than being bolted on, with clear boundaries and responsibility placement between core services and extensions. Common concerns include lifecycle hooks, configuration-driven loading, registration patterns, public exports, and compatibility between core services and plugins. Typical plugin families include entity plugins for durable content types, service plugins for tools and integrations, and interface plugins for transports and routes such as MCP, Discord, A2A, and webserver endpoints.
