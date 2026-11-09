---
question: How do I set up and operate a Brain?
status: draft
asked: 15
---
# FAQ

## Answer
\# Setting up and operating a Brain

A Brain is a self-hosted AI runtime whose durable knowledge is stored as Markdown. Configuration, enabled capabilities, identity, permissions, integrations, and site settings are declared explicitly in `brain.yaml`.

\## 1. Install the CLI

Prerequisites:

- Bun 1.4.0 or newer
- An API key supported by the configured AI provider

```bash
bun add -g @rizom/brain
```

\## 2. Scaffold an instance

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

\## 3. Configure secrets

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

\## 4. Start and test locally

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

\## 5. Configure access and permissions

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

\## 6. Connect interfaces

Interfaces are enabled by capability bundles and configured under `plugins:`.

\### Web and Studio

When enabled, the shared webserver provides routes such as:

```text
http://localhost:8080/
http://localhost:8080/studio
http://localhost:8080/dashboard
http://localhost:8080/mcp
http://localhost:8080/a2a
```

\### MCP

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

\### Discord and Slack

The chat plugin supports Discord and Slack. Configure credentials through environment variables and adapter settings in `brain.yaml`.

Recommended production safeguards:

- require mentions by default;
- restrict allowed channels;
- disable DMs unless they are intentional;
- grant trusted or admin access only to users who need uploads or write operations.

\### A2A

A2A exposes:

```text
/.well-known/agent-card.json
/a2a
```

You can connect an external Brain through its exact domain, approve it, and then call it. Outbound contact approval is separate from inbound trust.

\## 7. Operate content and tools

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

\## 8. Deploy to a server

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

\## 9. Maintain and recover

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

\## Recommended reading order

1. Getting Started
2. Feature Overview
3. Content Management
4. Interface Setup
5. Customization Guide
6. Deployment Guide

The current release is in the pre-stable `0.x` series, so configuration and extension APIs may change between minor releases.

## Sources

- [Getting Started](doc:getting-started)
- [Interface Setup](doc:interface-setup)
- [Feature Overview](doc:feature-overview)
- [Deployment Guide](doc:deployment-guide)

## Alternative answers

### Alternative answer 1

#### Answer
A brain is a private AI runtime whose durable knowledge is Markdown.

**Setup:**
1. Install Bun 1.4+ and obtain an API key.
2. Install the CLI: `bun add -g @rizom/brain`
3. Scaffold an instance: `brain init my-brain --recipe personal`
4. Enter the directory, set `AI_API_KEY` in `.env`, and run `brain start`.
5. Customize `brain.yaml`, starter content, site/theme files, and integrations as needed.

Choose a recipe—`headless`, `personal`, `professional`, or `team`—to select the initial capability bundles. For deployment, bootstrap certificates and push secrets before launching.

**Source:** [Getting Started](https://docs.rizom.ai/docs/getting-started) (public documentation).

### Alternative answer 2

#### Answer
A Brain is a private AI runtime whose durable knowledge is Markdown. To set one up:

1. Install Bun 1.4+ and an API key.
2. Install the CLI: `bun add -g @rizom/brain`
3. Initialize an instance, for example: `brain init my-brain --recipe personal`
4. Configure `.env` with `AI_API_KEY`, then run `brain start`.
5. Customize `brain.yaml`, seed content, interfaces, themes, and integrations.
6. For production, bootstrap certificates/secrets and use the deployment scaffolding.

Operate it through the CLI—especially `brain start`, `brain chat`, diagnostics, configuration, content synchronization, and deployment commands. The recommended documentation path is **Getting Started → Feature Overview → Content Management → Interface Setup → Deployment Guide**.

**Sources:** [Getting Started](https://docs.rizom.ai/docs/getting-started); [Documentation index](https://docs.rizom.ai/docs).

### Alternative answer 3

#### Answer
Setting up a brain is a staged process: install the CLI, initialize a brain, configure its `brain.yaml`, connect interfaces and tools, then start it locally or deploy it. Operating one means maintaining content, checking diagnostics and services, managing authentication and secrets, and monitoring deployment health.

**Sources:** [Documentation index](https://docs.rizom.ai/docs/index) (public `doc`, “Documentation”); **Brain Operations** (public `topic`).

### Alternative answer 4

#### Answer
\## Set up a new brain

The **Getting Started** doc recommends Bun 1.4.0 or newer and an API key supported by your configured AI provider.

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Set `AI_API_KEY` in `.env`, then start it:

```bash
brain start
```

On first startup, the terminal prints a one-time `/setup` link. Open it to register your passkey.

Choose a recipe based on what you need:

- `headless` — core capabilities
- `personal` — core, media, web, chat
- `professional` — adds automation, site, publishing, and federation
- `team` — includes team-oriented capabilities, plus docs and action board

For example, initialize a team brain with `brain init my-brain --recipe team`. Add `--deploy` if you want deployment scaffolding. `brain init` creates `brain.yaml`, starter content, package and environment files, and—when applicable—site files.

If you want setup links and invitations sent by email, configure `SETUP_EMAIL_TO`, `SETUP_EMAIL_API_KEY` (a Resend API key), and `SETUP_EMAIL_FROM` (a verified Resend sender). Otherwise, team members can be added through **Admin → Add a person** using a manual invite link.

Source: [Getting Started](https://docs.rizom.ai/docs/getting-started)

### Alternative answer 5

#### Answer
Install the CLI, scaffold an instance, add your AI key, then start it:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
cp .env.example .env
```

Set `AI_API_KEY` in `.env`, then run:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register your passkey and set up the first Admin. Choose a different recipe if you have a different use case: `headless`, `professional`, or `team`. Recipes scaffold the configuration and starter content; review the generated `brain.yaml` for the actual bundle selection.

For a server deployment, scaffold deployment files with `brain init my-brain --recipe professional --deploy`, then follow the **Deployment Guide**. For the full local setup and recipe details, see **Getting Started**.

### Alternative answer 6

#### Answer
For a local setup, install the CLI, scaffold an instance, add your AI API key, and start it:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Copy `.env.example` to `.env` and set `AI_API_KEY`, then run:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register a passkey and set up the first Admin. To receive setup links by email, configure `SETUP_EMAIL_TO`, `SETUP_EMAIL_API_KEY`, and `SETUP_EMAIL_FROM`.

Choose a recipe based on your needs:

- `headless` — core capabilities only
- `personal` — personal knowledge and chat
- `professional` — publishing and website capabilities
- `team` — collaborative features, plus docs and action board

To use a different recipe, replace `personal` in the `brain init` command. Recipes scaffold the instance; the generated `brain.yaml` records the bundles that determine runtime behavior.

### Alternative answer 7

#### Answer
Install the Brain CLI and scaffold a local instance:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Set `AI_API_KEY` in `.env`, then start the brain:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register your passkey.

Choose a recipe for your use case: `headless`, `personal`, `professional`, or `team`. The `brain init` command creates configuration, seed content, environment templates, and—when relevant—site files. Review the generated `brain.yaml`: the recipe provides scaffolding, while the selected bundle and configuration determine what the brain runs.

For a deployed setup, initialize with `--deploy` and follow the Deployment Guide. For more setup details and options, see Getting Started.

### Alternative answer 8

#### Answer
For a local brain, install the CLI and create a brain with the personal recipe:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Set `AI_API_KEY` in the generated `.env` file, then start the brain:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register your passkey and set up the first Admin. The generated `brain.yaml` makes the selected capability bundles and instance configuration explicit; recipes are scaffolding.

For a team or publishing-focused brain, use `--recipe team` or `--recipe professional` instead. See the **Getting Started** documentation for generated files and configuration, or the **Deployment Guide** to run it on a server.

### Alternative answer 9

#### Answer
\## Set up a brain locally

You’ll need **Bun 1.4.0 or newer** and an API key supported by the configured AI provider.

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Set `AI_API_KEY` in the generated `.env`, then start the brain:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register your passkey and set up the first Admin.

\### Choose a recipe

- **`headless`** — core capabilities; a minimal, non-web setup.
- **`personal`** — core, media, web, and chat.
- **`professional`** — adds automation, site, publishing, and federation.
- **`team`** — includes team collaboration, docs, and action-board capabilities.

To scaffold a team brain instead, run `brain init my-brain --recipe team`. Recipes are scaffolding: `brain init` writes the explicit bundle selection into `brain.yaml`, which determines what the instance runs.

\### What gets created

The scaffold includes `brain.yaml`, starter markdown in `seed-content/`, a pinned package dependency, environment templates, and supporting config files. You can add a content repository, connect an interface such as Discord, or customize the site and theme afterward. For deployment, use `brain init my-brain --deploy` and follow the deployment steps.

See [Getting Started](/docs/getting-started) for full setup details and the [Deployment Guide](/docs/deployment-guide) for deploying to a server.

### Alternative answer 10

#### Answer
The quickest way to set up a new brain is to scaffold one with the CLI and run it locally:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Add your AI provider key to `.env`:

```env
AI_API_KEY=your-key
```

Then start the brain:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register your passkey.

Choose a recipe based on your needs:

- `headless` — core capabilities only
- `personal` — core, media, web, and chat
- `professional` — adds automation, site, publishing, and federation
- `team` — collaboration-oriented setup, plus docs and action-board

For a server deployment, scaffold with `brain init my-brain --recipe professional --deploy --domain your-domain.com`, then follow the generated setup in the Deployment Guide. Recipes provide starter configuration and content; the instance’s actual capabilities are recorded in `brain.yaml`.

Sources: [Getting Started](/docs/getting-started), [Deployment Guide](/docs/deployment-guide), [CLI Reference](/docs/cli-reference).

### Alternative answer 11

#### Answer
\## Set up a new brain

The **Getting Started** doc gives the quickest path to a local instance:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Set `AI_API_KEY` in the generated `.env`, then start it:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register a passkey and set up the first Admin.

`brain init` creates the instance configuration (`brain.yaml`), seed-content directory, package files, and environment templates. Recipes such as `personal`, `professional`, and `team` are scaffold-time starting points; the resulting `brain.yaml` explicitly selects the capabilities the instance uses.

For a hosted setup, add `--deploy` when initializing, then follow the **Deployment Guide**. For configuration details, see **brain.yaml Reference**.

### Alternative answer 12

#### Answer
\## Set up a brain locally

The **Getting Started** guide recommends this quick start:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Copy `.env.example` to `.env` if needed, then set `AI_API_KEY`—the only required variable for first start—and run:

```bash
brain start
```

On first start, the brain prints a one-time `/setup` link in the terminal. Open it to register the first passkey.

Choose a recipe to suit your use:

- `headless` — core capabilities
- `personal` — core, media, web, and chat
- `professional` — adds automation, site, publishing, and federation
- `team` — collaboration-focused setup with docs and action board

For example, use `brain init my-brain --recipe professional` instead if you want publishing and a site. Recipes scaffold the instance; the selected bundles are written explicitly in `brain.yaml`.

For a server deployment, `brain init` also accepts `--deploy` and `--domain`. See the **Deployment Guide** for the deployment workflow, and the **brain.yaml Reference** for configuration details.

### Alternative answer 13

#### Answer
The **“Running your own brain”** guide gives this quick local setup:

1. Install Bun 1.4 or later and get an AI API key.
2. Install the CLI and create an instance:
   ```bash
   bun add -g @rizom/brain
   brain init my-brain --recipe personal
   cd my-brain
   ```
3. Put `AI_API_KEY=...` in `.env`, then start the brain:
   ```bash
   brain start
   ```
4. Open the one-time setup link printed in the terminal and register a passkey.

Choose a recipe based on what you want the brain to do: `personal` for private chat, `professional` for a site and publishing, `team` for collaboration, or `headless` without the web interface.

Your content lives in `brain-data/`: top-level Markdown files become notes; typed content goes in folders such as `brain-data/link/`, and images go in `brain-data/image/`. Add a content Git repository with `--content-repo owner/name`. For a server deployment, initialize with `--deploy --domain your.domain`.

For exact details, see [Getting Started](/docs/getting-started) and [Running your own brain](/guides/self-hosting).

### Alternative answer 14

#### Answer
\## Set up a brain locally

1. Install **Bun 1.4.0 or newer** and get an API key supported by your configured AI provider.
2. Install the CLI and scaffold an instance:
   ```bash
   bun add -g @rizom/brain
   brain init my-brain --recipe personal
   cd my-brain
   ```
3. Put your key in `.env` as `AI_API_KEY`.
4. Start it:
   ```bash
   brain start
   ```
5. On first start, open the one-time `/setup` link printed in the terminal and register your passkey.

Choose a recipe based on what you need: `headless` (core only), `personal`, `professional`, or `team`. Recipes are scaffolding: `brain init` writes the selected bundles explicitly into `brain.yaml` and copies starter content into `seed-content/`.

For email-delivered setup links and invitations, configure `SETUP_EMAIL_TO`, `SETUP_EMAIL_API_KEY` (a Resend API key), and `SETUP_EMAIL_FROM` (a verified sender). For other configuration options and deployment next steps, see **Getting Started**.
