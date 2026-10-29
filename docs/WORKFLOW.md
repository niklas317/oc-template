# Engineering Workflow

This file describes the agreed development process. Dedicated skills, commands, and agents will implement parts of it later; they are **not assumed to exist yet**.

## Requirements & Planning

- Use structured, testable requirements for substantial features; keep trivial changes lightweight. Sphinx-Needs is optional for projects needing formal traceability.
- Agree on architecture, acceptance criteria, verification strategy, and small milestones before substantial implementation.
- Declare both **structural scope** (files, directories, dependencies) and **behavioral scope** (functions, interfaces, effects). Permission to edit a file is not permission to redesign it.

## Implementation & Verification

- The implementation agent works autonomously within the approved milestone and scope, including evidence-based debugging and repeated testing.
- Preserve unrelated behavior. Ask before scope expansion, requirement changes, or significant architectural deviations.
- Select suitable software tests, static checks, and simulations; report exactly what passed, failed, or could not run.
- A separate **read-only review subagent** should inspect changes against requirements and engineering standards (implementation pending).
- Fix blocking review findings within approved scope and reverify; present optional improvements for operator decision.

## Milestone Acceptance & Git

- After each milestone, summarize changed files, behavior, tests, review findings, and remaining limitations. Detail should reflect the change's impact.
- The agent can mark work **ready for approval**, but only the operator can **accept** it. Wait for acceptance before starting the next milestone.
- Acceptance authorizes one focused local commit containing approved changes only.
- Pushing, merging, shared-history rebasing, and destructive Git operations require separate approval.

## External Verification

Use when a test requires another machine, unavailable compute, or human-operated hardware.

1. Prepare a test branch `test/YYYY-MM-DD-case-name` (add a suffix if needed). Intermediate commits on this branch do **not** signify milestone acceptance.
2. Create `RESULTS.md` on that branch with test/requirement IDs where available, objective, prerequisites, exact procedure, expected outcomes, and blank fields for actual results, logs, observations, and outcome.
3. Request approval before pushing the test branch. One explicit approval is enough for that push; no standing push permission is implied.
4. The operator pulls the branch, runs the external tests, fills in `RESULTS.md`, commits the evidence, and pushes it back.
5. The agent retrieves the findings and continues only within the previously approved implementation scope. Failed, missing, or inconclusive tests remain visible.

### Real-World Verification

- Identify physical validation needs during requirements engineering. Passing simulation is **not** equivalent to physical validation.
- If hardware verification is required, produce a **Real-World Verification Request** with test objective, safety/prerequisites, steps, expected results, and required evidence.
- Only the operator executes physical tests. The agent analyzes reported results, but never controls the hardware.

## Session Handoff

- Do not maintain a continuous development journal.
- On explicit `/handoff` invocation (to be implemented), create or update `docs/HANDOFF.md` with current objective, decisions, state, changed files, verification, blockers, and next steps. Exclude secrets.
- When resuming, compare the handoff against the repository and Git state instead of blindly trusting it.
