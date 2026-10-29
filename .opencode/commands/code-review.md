---
description: Run independent standards and specification reviews of code changes.
subagent: false
---

Load the `code-review` skill and follow its review procedure.

Review target: $ARGUMENTS

If no target is specified, review the current working-tree changes, including staged, unstaged, and untracked files.

Remain in the current primary session.

Prepare the review context and invoke `code-reviewer` separately for:
1. Standards review
2. Specification review

Use independent child contexts, preferably in parallel.

Collect both results and present the findings according to the skill.

Do not mark the milestone as accepted.
