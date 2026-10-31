---
question: How do I set up a new brain?
status: draft
asked: 2
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

## Alternative answers

### Alternative answer 1

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
