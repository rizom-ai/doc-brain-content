---
question: How do I set up a new brain?
status: draft
asked: 1
---
# FAQ

## Answer
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

## Sources

- [Getting Started](https://docs.rizom.ai/docs/getting-started "doc:getting-started")
- [Deployment Guide](https://docs.rizom.ai/docs/deployment-guide "doc:deployment-guide")
