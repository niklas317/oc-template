
---
name: code-review
description: Review code changes independently against project standards and requirements using two subagent reviews.
metadata:
  source_repository: "https://github.com/mattpocock/skills"
  source_commit: "59db609eb1e18aaf59b63284d0e52255aff0c63c"
  source_path: "skills/engineering/code-review/SKILL.md"
  license: "MIT"
  license_file: "licenses/mattpocock-skills.LICENSE"
  adapted: "true"
---

# Code Review

Review changes on two independent axes:

1. **Standards:** Correctness, safety, maintainability, and compliance with documented coding standards.
2. **Specification:** Compliance with requirements, acceptance criteria, and approved implementation scope.

Keep the two reviews independent.

## 1. Determine Review Scope

- Identify the changes requested for review.
- By default, include staged, unstaged, and untracked changes.
- If a Git reference is supplied, compare against that reference.
- Exclude unrelated changes and generated artifacts.
- Establish the relevant diff and changed-file list.

Do not require committed changes.

## 2. Gather Context

Identify:
- Relevant requirements and acceptance criteria.
- Approved structural and behavioral scope.
- AGENTS.md and relevant coding standards.
- Relevant architecture and interface documentation.

Use local documentation. Do not require an external issue tracker.

If specifications are missing, report that limitation.

## 3. Independent Reviews

Invoke the `code-reviewer` subagent twice, with fresh contexts.

Prefer parallel execution when available.

### Standards Review

Provide the diff, changed-file list, and relevant standards.

Check:
- Correctness, regressions, and edge cases.
- Concurrency, memory safety, and error handling.
- Interface compatibility and performance risks.
- Violations of documented coding standards.
- Relevant code smells and unnecessary complexity.

Treat code smells as recommendations, not automatic violations.

### Specification Review

Provide the diff, requirements, acceptance criteria, and approved scope.

Check:
- Missing or partially implemented requirements.
- Incorrect behavior relative to the specification.
- Unrequested changes or scope expansion.
- Missing verification for acceptance criteria.
- Changes that violate approved interfaces or behavior.

If no specification is available, report this axis as not evaluated.

## 4. Review Boundaries

- Subagents must not modify files.
- Subagents must not spawn additional agents.
- Do not let the implementation agent perform either review itself.
- Every finding must reference concrete evidence.
- Do not invent findings or claim checks were executed.

## 5. Report

Present separate sections:

### Standards
### Specification

For each finding include:
- Severity: Blocking or Optional
- File and line reference
- Problem and impact
- Recommended correction

Keep reports concise and actionable.

The main agent may resolve blocking findings within the approved milestone and scope, then request another independent review.

Do not automatically implement optional improvements.

A successful review does not imply milestone acceptance.
Only the operator may approve completion.
