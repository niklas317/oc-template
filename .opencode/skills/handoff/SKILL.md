---
name: handoff
description: Create a concise, repository-local session handoff when explicitly requested by the operator.
license: MIT
compatibility: opencode
metadata:
  source_repository: "https://github.com/mattpocock/skills"
  source_commit: "59db609eb1e18aaf59b63284d0e52255aff0c63c"
  source_path: "skills/productivity/handoff/SKILL.md"
  adapted: "true"
  license_file: "licenses/mattpocock-skills.LICENSE"
---

# Session Handoff

Only create a handoff when the operator explicitly requests it.

Write or replace `docs/HANDOFF.md` in the current repository, without modifying unrelated files. If a handoff already exists, preserve still-relevant information and replace outdated state.

Capture only what the next session needs:
- Current objective, approved scope, milestone state, and outstanding approvals.
- Decisions and their rationale, unresolved questions, and blockers.
- Relevant files, branch, commit, and working-tree changes; distinguish committed from uncommitted work.
- Checks performed, results, limitations, and next steps.
- Suggested existing skills to load next, if relevant.

Reference existing specs, plans, ADRs, issues, commits, and diffs rather than copying them. Redact secrets and personal information. Never treat unfinished work as accepted or commit the handoff automatically.

If the operator specifies what the next session will focus on, prioritize that context.

When resuming from a handoff, verify its claims against current project files and Git state before proceeding.
