---
question: How do I set up and operate a Brain?
status: draft
asked: 1
sources:
  - id: 'doc:getting-started'
    title: Getting Started
    excerpt: |-
      ---
      title: Getting Started
      section: Start here
      order: 10
      sourcePath: packages/brain-cli/docs/getting-started.md
      description: >-
        A brain is a private AI runtime whose durable knowledge is markdown. O...
  - id: 'doc:interface-setup'
    title: Interface Setup
    excerpt: |-
      ---
      title: Interface Setup
      section: Interfaces
      order: 80
      sourcePath: docs/interface-setup.md
      description: >-
        Interfaces are how users, tools, web clients, and peer agents talk to a
        running brain. ...
  - id: 'doc:feature-overview'
    title: Feature Overview
    excerpt: |-
      ---
      title: Feature Overview
      section: Start here
      order: 15
      sourcePath: docs/feature-overview.md
      description: >-
        brains is a self-hosted AI knowledge system built around content you own. A
        brain can...
  - id: 'doc:deployment-guide'
    title: Deployment Guide
    excerpt: >-
      ---

      title: Deployment Guide

      section: Start here

      order: 40

      sourcePath: packages/brain-cli/docs/deployment-guide.md

      description: Deploy a brain to a server using the scaffolded GitHub
      Actions + Kamal fl...
---
# Setting up and operating a Brain

A Brain is a self-hosted AI runtime whose durable knowledge is stored as Markdown. Configuration, enabled capabilities, identity, permissions, integrations, and site settings are declared explicitly in `brain.yaml`.

## 1. Install the CLI

Prerequisites:

- Bun 1.4.0 or newer
- An API key supported by the configured AI provider

```bash
bun add -g @rizom/brain
```

## 2. Scaffold an instance

Choose a recipe based on the intended use:

```bash
brain init my-brain --recipe personal
```

Available recipes:

| Recipe | Main capabilities |
|---|---|
| `headless` | Core knowledge runtime only |
| `personal` | Core, media, web, and chat |
| `professional` | Personal capabilities plus automation, site, publishing, and federation |
| `team` | Collaboration-oriented configuration, including shared-memory policy |

Other useful options:

```bash
brain init my-brain \
  --recipe professional \
  --domain brain.example.com \
  --content-repo github:owner/brain-data \
  --deploy
```

The command creates:

- `brain.yaml` — explicit bundle and plugin configuration
- `seed-content/` — initial Markdown content
- `package.json`
- `.env.example` and `.env.schema`
- TypeScript and Git configuration
- Optional deployment files when using `--deploy`

Recipes are scaffolding conveniences; the generated `brain.yaml` is the runtime source of truth.

## 3. Configure secrets

```bash
cd my-brain
cp .env.example .env
```

Set at least:

```bash
AI_API_KEY=your-provider-key
```

Keep secrets in environment-backed configuration. Keep non-secret settings—bundles, plugins, permissions, domains, and site configuration—in `brain.yaml`.

A typical configuration begins like:

```yaml
brain: brain
bundleContract: capability-bundles-v1
anchor: person
kind: professional

bundles:
  - core
  - media
  - web
  - chat

plugins:
  directory-sync:
    seedContentPath: ./seed-content
```

If migrating an older configuration, preview the canonical form without modifying the file:

```bash
brain config migrate
```

## 4. Start and test locally

Start the instance:

```bash
brain start
```

Start with a terminal chat session:

```bash
brain chat
```

Run a plugin lifecycle smoke test without starting daemons or workers:

```bash
brain start --startup-check
```

Useful local checks include:

```bash
brain tool system_status
brain tool system_search '{"query":"what content exists?"}'
```

The runtime stores durable content under `brain-data/`. SQLite supports indexing, semantic search, jobs, conversations, authentication, and runtime state, but does not replace the portable Markdown files.

## 5. Configure access and permissions

Permissions distinguish public use from trusted and administrative operations. Configure exact identities and interface patterns in `brain.yaml`, for example:

```yaml
permissions:
  anchors:
    - "cli:*"
    - "mcp:stdio"

  trusted:
    - "discord:123456789012345678"

  rules:
    - pattern: "mcp:http"
      level: public
    - pattern: "discord:*"
      level: public
    - pattern: "a2a:*"
      level: public
```

Use:

- `public` for ordinary read-oriented interaction
- `trusted` for selected collaborators and write-capable users
- `admin` for administration and privileged operations
- `anchors` for identities representing the Brain’s owner or subject

For a fresh authenticated web/MCP instance, first boot prints a one-time `/setup` URL. The first administrator opens it locally and registers a passkey. Prefer OAuth/passkeys over the deprecated static `MCP_AUTH_TOKEN` fallback.

Keep authentication state persistent and outside `brain-data`, typically under the runtime data volume.

## 6. Connect interfaces

Interfaces are enabled by capability bundles and configured under `plugins:`.

### Web and Studio

When enabled, the shared webserver provides routes such as:

```text
http://localhost:8080/
http://localhost:8080/studio
http://localhost:8080/dashboard
http://localhost:8080/mcp
http://localhost:8080/a2a
```

### MCP

HTTP MCP is normally available at:

```text
http://localhost:8080/mcp
```

The default MCP mode is `basic`, where clients use the agent-facing `chat` and `confirm` tools. Raw tools are only exposed in local/operator `debug` mode, which requires Admin access.

For stdio clients:

```yaml
plugins:
  mcp:
    transport: stdio
```

Example client configuration:

```json
{
  "mcpServers": {
    "mybrain": {
      "command": "brain",
      "args": ["start"],
      "cwd": "/absolute/path/to/my-brain"
    }
  }
}
```

### Discord and Slack

The chat plugin supports Discord and Slack. Configure credentials through environment variables and adapter settings in `brain.yaml`.

Recommended production safeguards:

- require mentions by default;
- restrict allowed channels;
- disable DMs unless they are intentional;
- grant trusted or admin access only to users who need uploads or write operations.

### A2A

A2A exposes:

```text
/.well-known/agent-card.json
/a2a
```

You can connect an external Brain through its exact domain, approve it, and then call it. Outbound contact approval is separate from inbound trust.

## 7. Operate content and tools

The main operational capabilities are:

- capture text, URLs, uploads, and previous responses;
- search semantically or retrieve exact records;
- create, update, generate, publish, and delete entities according to permissions;
- synchronize Markdown directories and optional Git repositories;
- inspect background jobs and progress;
- publish selected content through site, blog, deck, social, and newsletter workflows.

Useful CLI commands:

```bash
brain tool system_status
brain tool system_search '{"query":"recent posts"}'
brain diagnostics search
brain diagnostics usage
brain eval
brain eval --compare
```

Brain-specific commands depend on the enabled bundles and plugins:

```bash
brain sync
brain status
```

For a deployed instance, use remote mode:

```bash
brain --remote https://brain.example.com status
brain --remote https://brain.example.com search "topics"
brain --remote https://brain.example.com --token "$TOKEN" sync
```

## 8. Deploy to a server

For the documented self-hosted deployment path:

```bash
brain init my-brain --deploy --domain brain.example.com
cd my-brain
```

The deployment scaffold includes Docker, Kamal, and GitHub Actions files.

Typical preparation:

```bash
brain ssh-key:bootstrap --push-to gh
brain secrets:push --push-to gh --dry-run
brain secrets:push --push-to gh
brain cert:bootstrap --push-to gh
```

The generated workflow:

1. Builds and publishes an immutable image to GHCR.
2. Provisions or reuses the server.
3. Updates Cloudflare DNS.
4. Deploys the exact published commit with Kamal.
5. Verifies origin TLS and readiness.

The deployment exposes:

```text
/health/live     # dependency-free liveness
/health/ready    # web-serving readiness
/health/operate  # broader operational health
```

For a simple Docker deployment:

```bash
docker run -d \
  --name mybrain \
  -p 4321:8080 \
  -v ~/brain-data:/app/brain-data \
  -v ~/brain.yaml:/app/brain.yaml \
  --env-file .env \
  ghcr.io/<owner>/<repo>:latest
```

## 9. Maintain and recover

Common operational commands:

```bash
kamal deploy
kamal rollback
kamal app logs
kamal details
```

For authentication recovery, stop the Brain first:

```bash
brain auth reset-passkeys --yes
brain auth reinitialize-access --yes
```

After recovery, restart the instance. Authentication storage must remain outside `brain-data`.

## Recommended reading order

1. Getting Started
2. Feature Overview
3. Content Management
4. Interface Setup
5. Customization Guide
6. Deployment Guide

The current release is in the pre-stable `0.x` series, so configuration and extension APIs may change between minor releases.
