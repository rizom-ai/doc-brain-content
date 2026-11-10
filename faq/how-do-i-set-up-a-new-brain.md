---
question: How do I set up a new brain?
status: draft
asked: 1
---
# FAQ

## Answer
The **Getting Started** guide gives the local quick start:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Set `AI_API_KEY` in the generated `.env` file, then start the brain:

```bash
brain start
```

On first start, the brain prints a one-time `/setup` link in the terminal. Open it to register your passkey.

Choose another recipe if it better fits your use: `headless`, `professional`, or `team`. You can also add `--deploy` to `brain init` for deployment scaffolding. For available options and next steps, such as connecting a content repository or configuring a domain, see [Getting Started](/docs/getting-started).

## Sources

- [Getting Started](https://docs.rizom.ai/docs/getting-started "doc:getting-started")
