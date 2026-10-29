
---
name: external-test
description: Use when verification requires unavailable hardware, GPU, compute resources, or another machine. Prepare an operator-executed test handoff and evaluate returned results.
---

# External Verification

Use when required verification cannot be completed locally.
Perform feasible local checks before requesting external testing.

## 1. Prepare

- Identify what remains unverified and why.
- Define the test objective, acceptance criteria, required environment, and expected results.
- Specify reproducible test steps and required logs or measurements.
- Leave physical hardware setup, safety assessment, and test execution to the operator.

## 2. Handoff

If verification requires transferring code to another machine:

1. Propose a branch named `test/YYYY-MM-DD-case-name`.
2. Declare the test candidate scope, verification procedure, and expected results.
3. Request approval for the complete handoff, including branch creation, commit, and push.
4. Once approved:
   - Create the test branch without losing unrelated work.
   - Write `RESULTS.md` containing:
     - Test objective and relevant requirements
     - Environment and prerequisites
     - Test procedure and expected results
     - Empty fields for actual results, observations, and logs
     - Outcome: Pending / Passed / Failed / Inconclusive
   - Commit only the approved test candidate and documentation.
   - Push the designated test branch.

The approval applies only to this handoff and branch.
Any scope expansion requires renewed approval.
Intermediate test commits do not imply milestone acceptance.

If no code transfer is necessary, provide the verification instructions directly without creating a branch.

## 3. Evaluate

After the operator returns the completed results:

- Verify the tested revision and examine the evidence.
- Compare actual results against acceptance criteria.
- Report passed, failed, and inconclusive checks.
- Investigate failures within the approved scope.
- Request additional verification when evidence is insufficient.

## Constraints

- Never execute tests on connected physical hardware.
- Never infer success from missing results.
- Do not merge test branches or accept milestones.
- Preserve unrelated files, branches, and Git history.
- Follow AGENTS.md and the approved development workflow.
