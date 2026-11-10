---
question: How do I set up a new brain?
status: draft
asked: 2
---
# FAQ

## Answer
\## Set up a new brain

Follow the local quick start:

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

To choose another recipe, pass `--recipe` with one of these options: `headless`, `personal`, `professional`, or `team`. To include deployment scaffolding during initialization, add `--deploy`. The `brain init` command creates `brain.yaml`, seed content, dependency and environment files, and—depending on the recipe—site files.

For server deployment, see the Deployment Guide. For configuration options, see the `brain.yaml` Reference.

## Sources

- [Getting Started](https://docs.rizom.ai/docs/getting-started "doc:getting-started")
- [Deployment Guide](https://docs.rizom.ai/docs/deployment-guide "doc:deployment-guide")

## Alternative answers

### Alternative answer 1

#### Answer
\## Set up a brain locally

With **Bun 1.4.0 or newer** installed, run:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Add your AI provider key to `.env` as `AI_API_KEY`, then start the brain:

```bash
brain start
```

On first start, the brain prints a one-time `/setup` link. Open it to register your passkey.

Choose a recipe for your needs:

- `headless` — core capabilities
- `personal` — core, media, web, and chat
- `professional` — adds automation, site, publishing, and federation
- `team` — team capabilities, plus docs and action board

To use another recipe, replace `personal` in the `brain init` command. You can also pass `--deploy` to scaffold deployment files or `--domain your.example.com` to set the production domain.

See the **Getting Started** doc for full setup details and next steps.
