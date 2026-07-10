---
title: "Documentation"
section: "Start here"
order: 0
sourcePath: "docs/README.md"
slug: "index"
description: "Start here if you want to install brains, create a local brain, connect it to tools, or deploy it."
---

# brains documentation

Start here if you want to install `brains`, create a local brain, connect it to tools, or deploy it.

If you are new, read these in order:

1. [Getting Started](/docs/getting-started)
2. [Content Management](/docs/content-management)
3. [Interface Setup](/docs/interface-setup)
4. [Customization Guide](/docs/customization-guide)
5. [Deployment Guide](/docs/deployment-guide)

## Setup and operation

- [Getting Started](/docs/getting-started) — install the CLI, create a brain, and start it locally
- [CLI Reference](/docs/cli-reference) — commands such as `brain init`, `brain start`, `brain chat`, and `brain tool`
- [brain.yaml Reference](/docs/brain-yaml-reference) — the main configuration file
- [Deployment Guide](/docs/deployment-guide) — deploy to a server with the generated Docker/Kamal workflow

## Content

- [Content Management](/docs/content-management) — create, edit, sync, and publish markdown content
- [Directory Sync Git Overview](/docs/directory-sync-git) — git-style lifecycle and conflict policy for synced content directories
- [Entity Types Reference](/docs/entity-types-reference) — built-in content types and their fields
- [Entity Model](/docs/entity-model) — how markdown files, frontmatter, and schemas fit together

## Connecting clients and services

- [Interface Setup](/docs/interface-setup) — MCP, web, Discord, A2A, and local chat setup
- [MCP Inspector Guide](/docs/mcp-inspector-guide) — debug MCP connections and tool calls

## Customization

- [Customization Guide](/docs/customization-guide) — change presets, content, themes, sites, and plugins
- [Theming Guide](/docs/theming-guide) — theme tokens, CSS layers, and custom themes
- [Plugin System](/docs/plugin-system) — how built-in and custom plugins are organized
- [Plugin Quick Reference](/docs/plugin-quick-reference) — concise plugin API reference
- [External Plugin Authoring](/docs/external-plugin-authoring) — package and load external plugins

## Architecture

These are useful once you are extending or contributing to the framework:

- [Architecture Overview](/docs/architecture-overview)
- [Brain Models](/docs/brain-model)

## Status and contributing

- [Roadmap](https://github.com/rizom-ai/brains/blob/main/docs/roadmap.md) — maintainer roadmap and release priorities
- [Stability Policy](https://github.com/rizom-ai/brains/blob/main/STABILITY.md) — what is stable during the `0.x` series
- [Changelog](https://github.com/rizom-ai/brains/blob/main/CHANGELOG.md)
- [Known Issues](https://github.com/rizom-ai/brains/blob/main/KNOWN-ISSUES.md)
- [Contributing](https://github.com/rizom-ai/brains/blob/main/CONTRIBUTING.md)
- [Security](https://github.com/rizom-ai/brains/blob/main/SECURITY.md)

Maintainer planning notes, prototypes, and design mockups still live under `docs/plans/`, `docs/prototypes/`, and `docs/design/`, but they are not part of the primary documentation path.

### Console design references

- [Console unification mockups](https://github.com/rizom-ai/brains/blob/main/docs/console-unification-mockups.html) — preserved desktop reference for the shared console sheet and chrome
- [Responsive console mockups](https://github.com/rizom-ai/brains/blob/main/docs/console-responsive-mockups.html) — canonical desktop, tablet, and phone compositions for Dashboard, Chat, and CMS
