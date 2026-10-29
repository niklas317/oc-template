---
description: Inspect this repository and prepare its project-specific OpenCode setup
---

# Project setup

Prepare this repository to become a real project. Work only inside this repository.

1. Read `AGENTS.md`, `docs/PROJECT.md`, `opencode.json`, the README, and any existing source, manifests, and test configuration.
2. Identify the actual purpose and tech stack from evidence. Mark missing information as unknown; do not guess frameworks, package managers, architecture, secrets, or test commands.
3. Ask the user only for decisions that cannot be derived from existing files (for example: project goal, preferred stack, runtime, tests, deploy target).
4. Present a brief setup proposal first: suggested project structure, changes to `docs/PROJECT.md` and `AGENTS.md`, commands to verify, and any optional skill/MCP/subagent that solves a real need.
5. Stop and request explicit approval before editing project instructions or configuration. Do not install dependencies, call external services, or run destructive operations as part of planning.
6. After the user approves, update `docs/PROJECT.md` with confirmed facts. Update `AGENTS.md` only if generic rules need project-specific additions; keep it concise. Add no MCPs or subagents merely for completeness.
7. Summarize completed changes, open decisions, and the exact next action the user can take.

In all steps, follow the repository's permissions and restrictions. Never work outside the repository.
