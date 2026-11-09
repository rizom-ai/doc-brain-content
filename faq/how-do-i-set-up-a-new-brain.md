---
question: How do I set up a new brain?
status: draft
asked: 1
---
# FAQ

## Answer
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

## Sources

- [Getting Started](https://docs.rizom.ai/docs/getting-started "doc:getting-started")
- [CLI Reference](https://docs.rizom.ai/docs/cli-reference "doc:cli-reference")
- [Deployment Guide](https://docs.rizom.ai/docs/deployment-guide "doc:deployment-guide")
