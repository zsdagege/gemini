# AGENTS.md

## Repository workflow

Use this workflow for all code changes in this repository.

1. Never push changes directly to `main`.
2. Create or use a task branch named `codex/<short-task-name>`.
3. Keep each branch focused on one task.
4. Before committing, review the diff and make sure no secrets or local-only files are included.
5. Never commit API keys, tokens, credentials, `.env` files, or other sensitive values.
6. Run the repository checks before opening or updating a pull request:

   ```bash
   deno check src/deno_index.ts
   node --check src/api_proxy/worker.mjs
   node --input-type=module --check < src/index.js
   ```

7. If a check fails, fix the issue before requesting review.
8. Commit changes with a concise message describing the change.
9. Push the task branch and open a pull request targeting `main`.
10. In the pull request description, include:
    - what changed
    - why it changed
    - checks performed
    - known risks or follow-up work
11. Address review feedback on the same branch and rerun the checks.
12. Merge only after required checks and review are complete.

## Project notes

- The repository contains Deno and JavaScript runtime entry points.
- The documented Deno deployment entry point is `src/deno_index.ts`.
- Avoid changing deployment behavior unless the task explicitly requires it.
- Preserve compatibility with the existing OpenAI-compatible proxy behavior unless the task explicitly changes that contract.
