---
question: How do I set up a new brain locally?
status: draft
asked: 2
---
# FAQ

## Answer
\## Set up a brain locally

1. **Install Bun 1.4.0 or newer** and get an API key supported by your configured AI provider.
2. **Install the CLI and scaffold an instance.** Choose a recipe for the capabilities you need:

   ```bash
   bun add -g @rizom/brain
   brain init my-brain --recipe personal
   cd my-brain
   ```

   `personal` is a good starting point for an individual brain. Other options are `headless`, `professional`, and `team`.

3. **Set the AI key** in the generated `.env` file:

   ```env
   AI_API_KEY=your-key
   ```

4. **Start the brain:**

   ```bash
   brain start
   ```

   On first start, the terminal prints a one-time `/setup` link. Open it to register your passkey.

`brain init` creates `brain.yaml`, starter content, and the environment/configuration files. Recipes are scaffolding: you can adjust the selected bundles and configuration afterward. For a server deployment, scaffold deployment files with `brain init my-brain --deploy --domain your-domain.example`; see the **Deployment Guide** for deployment and secret setup.

Source: [Getting Started](/docs/getting-started).

## Sources

- [Getting Started](https://docs.rizom.ai/docs/getting-started "doc:getting-started")
- [Deployment Guide](https://docs.rizom.ai/docs/deployment-guide "doc:deployment-guide")

## Alternative answers

### Alternative answer 1

#### Answer
\## Set up a new brain

For a local instance, install the CLI, scaffold a brain, add your AI API key, and start it:

```bash
bun add -g @rizom/brain
brain init my-brain --recipe personal
cd my-brain
```

Copy `.env.example` to `.env` if needed, then set `AI_API_KEY`—the only required variable for a basic setup. Start the brain:

```bash
brain start
```

On first start, the terminal prints a one-time `/setup` link. Open it to register your passkey.

`brain init` creates the instance configuration (`brain.yaml`), seed content, package files, and environment templates. Recipes are scaffolding: they expand into explicit configuration in `brain.yaml`. You can customize its selected bundles and plugin settings there.

For email delivery of setup links and invitations, configure `SETUP_EMAIL_TO`, `SETUP_EMAIL_API_KEY`, and `SETUP_EMAIL_FROM` in the environment. Otherwise, team members can be invited from **Admin → Add a person** using a manual invite link.

For deployment, scaffold deployment files with `brain init my-brain --deploy --domain your-domain.example`; see the Deployment Guide for the full flow.

Sources: [Getting Started](/docs/getting-started), [Deployment Guide](/docs/deployment-guide).
