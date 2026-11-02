# oc-template
Project-local OpenCode configuration for new and existing repositories.

## Setup
Copy `AGENTS.md`, `opencode.json`, `.opencode/`, `docs/`, and `licenses/` into your repository. Merge conflicts; do not overwrite existing configuration blindly.
Run `opencode`, then `/project-setup`; apply approved changes with `/project-setup apply`.

## Included
- **Commands:** `project-setup`, `handoff`, `code-review`.
- **Skills:** `handoff`, `code-review`, `systematic-debugging`, `external-test`, `grilling`, `ros2-engineering`.
- **Agent:** Independent code reviewer.
- **Docs:** Project context, workflow, and environment policies.

## Blender MCP (optional)
Install and enable [Blender MCP](https://github.com/ahujasid/mcp-for-blender) on the host; install `uvx` in the VM and enable Blender in `opencode.json`.
Forward the port from the host: `ssh -N -o ExitOnForwardFailure=yes -R 127.0.0.1:9876:127.0.0.1:9876 USER@VM_IP`

## Adding Skills
Create `.opencode/skills/<name>/SKILL.md` with YAML `name` and `description` frontmatter followed by concise instructions.
For adapted skills, record the upstream URL, commit SHA, source path, and license; store upstream licenses in `licenses/`.

## LICENSE
MIT (`licenses/LICENSE`) for original template content; third-party skills retain their respective licenses.