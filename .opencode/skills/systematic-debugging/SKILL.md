---
name: systematic-debugging
description: Use when investigating bugs, failing tests, build errors, performance problems, or unexpected behavior. Find the root cause before implementing fixes.
license: MIT
metadata:
  source_repository: "https://github.com/obra/superpowers"
  source_commit: "bb92a77741419a4ab5f06e711a283343f1ada0c3"
  source_path: "skills/systematic-debugging/SKILL.md"
  license_file: "licenses/obra-superpowers.LICENSE"
  adapted: "true"
---

# Systematic Debugging

Find the root cause before attempting fixes.
Do not patch symptoms or make speculative changes.

## 1. Investigate

- Read relevant errors, logs, and stack traces.
- Reproduce the problem when possible.
- Inspect recent changes, dependencies, and environment differences.
- Trace failing data through component boundaries.
- Gather evidence before proposing a solution.
- If reproduction is impossible, identify missing evidence.

## 2. Analyze

- Find comparable working implementations.
- Compare expected and actual behavior.
- Identify differences and relevant assumptions.
- Trace the failure to its earliest identifiable cause.

## 3. Hypothesize

- Form one specific, evidence-based hypothesis.
- Design the smallest practical test to evaluate it.
- Change one variable at a time.
- If disproven, gather new evidence before continuing.
- Do not stack speculative fixes.

## 4. Fix and Verify

- Confirm the proposed fix addresses the root cause.
- Respect the approved structural and behavioral scope.
- Establish suitable regression verification.
- Apply the smallest necessary fix.
- Run relevant tests and check for regressions.
- Revisit the hypothesis if verification fails.

## Escalation

Continue investigating autonomously while making measurable progress.

Stop and consult the operator when:
- Attempts repeat without new evidence.
- Progress stalls or necessary information is unavailable.
- The solution requires expanded scope.
- Architectural assumptions appear incorrect.

Do not use an arbitrary retry limit.

## Constraints

- Follow AGENTS.md and the approved milestone workflow.
- Never execute tests on connected physical hardware.
- Use simulation or request operator-led verification.
- Do not perform unrelated refactoring.
- Report the root cause, fix, verification, and limitations.
- Do not mark a milestone as accepted.

## References

Original methodology:
https://github.com/obra/superpowers/tree/main/skills/systematic-debugging
