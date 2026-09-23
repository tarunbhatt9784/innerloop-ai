# Set Up a Claude Project

## Recommended topology

Create one private Claude Project named `InnerLoop AI - Personal`.

Add to Project knowledge:

- your raw journal PDFs as they are produced;
- selected files/folders from the public `innerloop-ai` repository;
- selected files/folders from your private `innerloop-memory` repository.

Paste `PROJECT_INSTRUCTIONS.md` into Claude's Project Instructions.

## GitHub repositories

### Public framework repo

Create `innerloop-ai` as a public repository. Connect the framework folders and root control files to the Claude Project.

### Private memory repo

Create `innerloop-memory` as a private repository. Start it from the supplied `innerloop-memory-template` folder. Never make this repository public.

## Important GitHub write caveat

Claude's standard Project GitHub integration is commonly used to sync repository files into Project knowledge. Whether Claude can write/commit back depends on the connector/surface and granted tool permissions. If your Project only has read access, ask Claude to emit a ready-to-save memory markdown block and commit it yourself, or run the workflow in a Claude surface with an approved GitHub write-capable connector/agent.

Never weaken repository privacy merely to enable automation.

## Daily operating prompt

Use `prompts/DAILY_RUN.md`. The prompt is intentionally short because the project instructions and framework files carry the durable behaviour.
