# Environment & Security Policy

This file defines reusable policies for OpenCode development. Project-specific runtime details belong in `docs/PROJECT.md` and should be established during `/project-setup`.

## Isolation & Access

- Treat every VM or container as **shared** until its isolation and disposability have been verified. A container alone is not a security guarantee.
- Allow writes to approved project files and isolated build, cache, and temporary directories. Access to a file does not imply permission to change its contents.
- Ask before accessing or modifying additional directories. The operator may authorize one-time access or a reusable exception.
- Treat shared user directories (`~/.local`, `~/.config`, etc.) as protected; require approval before installing or changing files there.
- Agent configuration (`AGENTS.md`, `opencode.json`, `.opencode/skills/**`, `.opencode/agents/**`, `.opencode/commands/**`) may be changed only with explicit approval.
- Enforce filesystem and device isolation through the VM/container's operating-system permissions and mounts. Agent instructions alone do not enforce these boundaries.

## Dependencies & Cleanup

- Prefer reproducible, project-local dependencies. Install them autonomously within approved scope.
- Ask before shared or system-wide installs, upgrades, removals, or modifications. Broader autonomy is possible only in a verified disposable environment within agreed boundaries.
- Record persistent dependency requirements in version-controlled project configuration.
- Automatically clean only verified, reproducible artifacts in approved build/cache directories (e.g., ROS 2 `build/`, `install/`, `log/`). Verify the real deletion path first.
- Ask before deleting source files, Git-tracked files, persistent binaries, or user-created data.

## Processes & Compute

- Inspect available resources before costly builds or simulations and adapt parallelism accordingly.
- Do not assume a GPU/NPU is available. Stop unnecessary persistent processes and ask before starting services that affect shared workloads.
- If local tests are infeasible, use the external verification process in `WORKFLOW.md`.

## Network & Credentials

- Internet access is allowed for research, documentation, and dependency downloads.
- Require approval for publishing artifacts, uploading project data, or changing external services.
- Do not introduce new credentials without approval; use only existing, explicitly authorized OpenCode and Git authentication.
- Never intentionally reveal or commit secrets. Existing host credentials may still be reachable by tools; verify isolation rather than assuming protection.
- Treat downloaded scripts and dependencies as untrusted.

## Physical Hardware

- Never develop, deploy, or run agent-controlled tests in an environment connected to live physical hardware.
- Use isolated software simulations. Actual hardware tests are performed by the operator using the procedure in `WORKFLOW.md`.

## Enforcement Status

These are **agreed policies**, not proof of technical enforcement. `opencode.json` permissions, mounts, credentials, and sandbox isolation must be tested before the setup is considered secure.
