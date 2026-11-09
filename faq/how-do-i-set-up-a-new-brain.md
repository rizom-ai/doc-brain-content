---
question: How do I set up a new brain?
status: draft
asked: 1
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
