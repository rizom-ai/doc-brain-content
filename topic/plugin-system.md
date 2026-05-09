---
title: Plugin System
---
A plugin system is a modular extension architecture that lets optional or external capabilities integrate into an application without changing its core logic. It defines stable extension points and clear contracts for discovering, loading, registering, and invoking plugins, preserving separation between the core system and add-on functionality.

A well-designed plugin system keeps the base application lightweight while enabling controlled growth through optional features, specialized behaviors, and third-party integrations. Plugin boundaries isolate extension logic from foundational services, reducing coupling and making it easier to evolve the system safely. Common concerns include lifecycle hooks, configuration-driven loading, registration patterns, public exports, compatibility between core services and plugins, and choosing the right extension shape for different needs.

Typical plugin families include entity plugins for durable content types, service plugins for tools and integrations, and interface plugins for transports and routes such as MCP, Discord, A2A, and webserver endpoints.
