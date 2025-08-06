# AI Developer Workflow

Guidelines and rules for using an AI assistant to plan and implement software features.

## Overview

This repository describes a three step workflow:

1. **Create a Product Requirements Document (PRD).**  
   See [`01-create-prd.md`](01-create-prd.md) for the standard process and [`01-create-prd-replit.md`](01-create-prd-replit.md) for Replit‑specific guidance.
2. **Generate a task list from the PRD.**  
   Instructions are in [`02-generate-tasks.md`](02-generate-tasks.md) and [`02-generate-tasks-replit.md`](02-generate-tasks-replit.md).
3. **Work through the task list.**  
   Rules for updating tasks and committing code are in [`03-process-task-list.md`](03-process-task-list.md) and [`03-process-tasks-replit.md`](03-process-tasks-replit.md).

All generated PRDs and task lists should be saved in the `/tasks` directory using the naming conventions described in the rule files.

## Repository structure

```
01-create-prd.md           – PRD generation rules
02-generate-tasks.md       – Task list creation rules
03-process-task-list.md    – Task management and commit rules
*-replit.md                – Variants of the rules tailored for the Replit platform
LICENSE                    – Project license
```

## Usage

1. Start with a brief feature description.
2. Follow the PRD rules to ask clarifying questions and write `prd-[feature].md` in `/tasks`.
3. Use the task generation rules to produce `tasks-prd-[feature].md`.
4. Implement each sub‑task sequentially while following the task processing rules.

## Testing and contributions

Before committing changes, run the project's tests (for example, `pytest` or `npm test`) and ensure they pass. Use conventional commit messages and reference relevant tasks when committing.

## License

This project is licensed under the [MIT License](LICENSE).
