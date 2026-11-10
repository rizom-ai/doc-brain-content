---
question: How do I set up a new brain locally?
status: draft
asked: 1
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
