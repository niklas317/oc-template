---
description: Onboard a new or existing repository for OpenCode development.
---

# Project Setup

Mode: `$ARGUMENTS` (default: `plan`).

Follow AGENTS.md and relevant project policies.
Do not initialize the original `oc-template` repository.

## Plan

1. Inspect the repository, architecture, dependencies, tests, documentation, and environment. Avoid secrets.
2. Interview the operator thoroughly about goals, design rationale, constraints, conventions, and intended workflows.
   - Ask in iterative rounds, pursuing meaningful details.
   - Don't ask what the repository already establishes.
   - Challenge ambiguities and conflicting assumptions.
3. Summarize your understanding and confirm it with the operator.
4. Propose minimal onboarding changes, specifying affected files and their intended purpose.
5. Await approval. Do not modify files.

## Apply

Only run with `apply` after explicit approval of a specific plan in this session.

- Implement only the approved changes, preserving existing configuration.
- Do not implement application features or install dependencies.
- Review the diff and report changes and remaining uncertainties.
- Await operator acceptance before committing.

For unknown modes, explain the supported options and stop.
