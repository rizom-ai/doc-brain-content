---
title: "Documentation"
section: "Use a brain"
order: 0
slug: "index"
description: "Start here if you want to install brains, create a local brain, connect it to tools, or deploy it."
---

# brains documentation

Start here if you want to install `brains`, create a local brain, connect it to tools, or deploy it.

Current release status: `0.2.0` alpha; stable nomination is pending the final authoring, live/eval, and deployment evidence listed in the [roadmap](https://github.com/rizom-ai/brains/blob/main/docs/roadmap.md).

If you are new, read these in order:

1. [Getting Started](/docs/getting-started)
2. [Feature Overview](/docs/feature-overview)
3. [Content Management](/docs/content-management)
4. [Interface Setup](/docs/interface-setup)
5. [Customization Guide](/docs/customization-guide)
6. [Deployment Guide](/docs/deployment-guide)

## Setup and operation

- [Getting Started](/docs/getting-started) — install the CLI, create a brain, and start it locally
- [Feature Overview](/docs/feature-overview) — user-facing guide to the knowledge, publishing, interface, integration, and operational features available today
- [CLI Reference](/docs/cli-reference) — commands such as `brain init`, `brain start`, `brain chat`, and `brain tool`
- [brain.yaml Reference](/docs/brain-yaml-reference) — the main configuration file
- [Deployment Guide](/docs/deployment-guide) — deploy to a server with the generated Docker/Kamal workflow

## Moving in

- [Moving in as a writer](/guides/writer) — years of essays and drafts
- [Moving in as a researcher](/guides/researcher) — notes, papers, and saved links
- [Moving in as a consultant](/guides/consultant) — client work, decks, and a profile
- [Moving in as a team](/guides/team) — what a team knows, in one place
- [Running your own brain](/guides/self-hosting) — your own server, content, and domain

## Content

- [Content Management](/docs/content-management) — create, edit, sync, and publish markdown content
- [Studio](/docs/studio) — the signed-in browser workspace for content, the Inbox, publishing, chat, and settings, plus guest Ask and the public dashboard
- [The Drive and Obsidian](/docs/drive-and-obsidian) — mount the brain as a network drive and keep an Obsidian vault in step
- [Directory Sync Git Overview](/docs/directory-sync-git) — git-style lifecycle and conflict policy for synced content directories
- [Entity Types Reference](/docs/entity-types-reference) — built-in content types and their fields
- [Entity Model](/docs/entity-model) — how markdown files, frontmatter, and schemas fit together
- [Seminars](/docs/seminars) — hold a structured discussion between peer brains and publish it

## Connecting clients and services

- [Interface Setup](/docs/interface-setup) — MCP, guest web chat, Discord, Slack, and Matrix chat, email, A2A, and the local chat REPL
- [Publishing Integrations and Site Add-ons](/docs/publishing-integrations) — LinkedIn, newsletters, AT Protocol, analytics, and stock photos, plus contact forms, quizzes, and other forms
- [MCP Inspector Guide](/docs/mcp-inspector-guide) — debug MCP connections and tool calls

## Customization

- [Customization Guide](/docs/customization-guide) — change bundles, content, themes, sites, and plugins
- [Site Mockup Migration](/docs/site-mockup-migration) — prototype a site in an AI coding tool, then move it into Brain routes, sections, content, and themes
- [Theming Guide](/docs/theming-guide) — theme tokens, CSS layers, and custom themes
- [Plugin System](/docs/plugin-system) — how built-in and custom plugins are organized
- [Package Authoring Quick Reference](/docs/plugin-quick-reference) — a checklist for choosing a definition family, with import, config, template, and lifecycle rules
- [Package Quickstart](/docs/package-quickstart) — write, test and compose one package with the two-stage definition
- [External Package Authoring](/docs/external-plugin-authoring) — package, test, and load your own plugin packages
- [External Site and Theme Authoring](/docs/external-site-authoring) — publish independently hosted site and theme packages through the public npm contract

## Architecture

These are useful once you are extending or contributing to the framework:

- [Architecture Overview](/docs/architecture-overview)
- [Brain Model](/docs/brain-model)
- [Agent Discovery](/docs/agent-discovery) — how a brain finds capabilities in itself and calls other brains
- [ATProto Lexicons](/docs/atproto-lexicons) — the AT Protocol lexicons published under `ai.rizom.brain`

## Status and contributing

- [Roadmap](https://github.com/rizom-ai/brains/blob/main/docs/roadmap.md) — maintainer roadmap and release priorities
- [Stability Policy](https://github.com/rizom-ai/brains/blob/main/STABILITY.md) — what is stable during the `0.x` series
- [Changelog](https://github.com/rizom-ai/brains/blob/main/CHANGELOG.md)
- [Known Issues](https://github.com/rizom-ai/brains/blob/main/KNOWN-ISSUES.md)
- [Contributing](https://github.com/rizom-ai/brains/blob/main/CONTRIBUTING.md)
- [Security](https://github.com/rizom-ai/brains/blob/main/SECURITY.md)

Maintainer planning notes, prototypes, and design mockups still live under `docs/plans/`, `docs/prototypes/`, and `docs/design/`, but they are not part of the primary documentation path.

### Console design references

- [Studio chrome mockup](https://github.com/rizom-ai/brains/blob/main/docs/studio-chrome-mockups.html) — current single-shell authenticated Studio and anonymous Dashboard direction
- [Console unification mockups](https://github.com/rizom-ai/brains/blob/main/docs/console-unification-mockups.html) — historical desktop reference for the retired cross-product strip
- [Responsive console mockups](https://github.com/rizom-ai/brains/blob/main/docs/console-responsive-mockups.html) — historical desktop, tablet, and phone compositions before Studio consolidation
