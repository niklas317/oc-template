# Development Workflow

This document describes how to use the OpenCode development environment in new or existing repositories.

General agent behavior is defined in `AGENTS.md`. Environment restrictions are defined in `docs/ENVIRONMENT.md`. Detailed procedures belong to their respective commands and skills.

## 1. Project Onboarding

Run `/project-setup` when introducing OpenCode to a repository.

- Analyze the existing codebase, architecture, tooling, and documentation.
- Conduct an iterative technical interview to establish project context.
- Document confirmed findings in `docs/PROJECT.md`.
- Propose configuration changes and apply them only after approval.

Preserve existing project conventions. Onboarding does not include application implementation or requirements engineering.

## 2. Development Cycle

Development follows a milestone-based workflow:

1. **Plan:** Establish the objective, acceptance criteria, architecture, and structural and behavioral change scope.
2. **Approve:** The operator agrees on the milestone and its boundaries.
3. **Implement:** The agent works autonomously within the approved scope, including debugging and appropriate testing.
4. **Review:** Independent subagents evaluate correctness, standards, and specification compliance through `code-review`.
5. **Verify:** Resolve blocking findings, repeat relevant checks, and document remaining limitations.
6. **Accept:** Present the result to the operator. Only explicit acceptance completes the milestone and authorizes its local commit.

Requirements may range from simple acceptance criteria to formal specifications. The appropriate level of detail depends on the project.

## 3. External Verification

When local verification is insufficient, use the `external-test` skill.

- Prepare a reproducible test procedure and identify required evidence.
- For cross-machine testing, obtain one approval covering creation, commit, and push of a dedicated `test/YYYY-MM-DD-case-name` branch.
- Record procedures and expected results in `RESULTS.md`.
- The operator executes external tests, records observations, and returns the results.
- Evaluate the findings before continuing development.

Physical hardware deployment and testing are exclusively operator-controlled. Intermediate test commits do not constitute milestone acceptance.

## 4. Session Continuity

Development normally continues within the current session until the milestone is resolved.

When context must be preserved across sessions or machines, invoke `/handoff` to create `docs/HANDOFF.md`.

On resumption, verify the handoff against the current repository and Git state before continuing.

No continuous development journal is required.