# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-howard/pull/78

**Branch**

fix/issue-65-async-mocks

## Eval iterations

**Run history**

1. Initial full evaluation: 17/20 agreement.
2. Targeted canary rerun of pkg-03, pkg-04, and pkg-16: 3/3 agreement.
3. Targeted canary rerun of pkg-08 and pkg-19: 2/2 agreement.
4. Final full evaluation: 20/20 scored items, meeting the required 18/20 threshold. The committed eval-run.txt records: agreement: 20/20 scored items (bar: 18/20: PASS).
   
**Package analysis**

pkg-16 — The initial rubric disagreed with the gold label because the pass conditions were too sensitive to differences in illustrative output strings. I revised the silent drift and not tested pass conditions to focus on whether the evidence supports the promised behavior, rather than requiring every illustrative output string to match exactly. The targeted canary rerun agreed with the gold label for pkg-16, and the final full evaluation achieved 20/20 agreement.

**Check rationale**

Exact quote from the silent drift check in tools/pr-precheck/rubric.md:

  Distinguish the promised behavior from illustrative examples of output: a wording or formatting difference     in an example is not by itself a material contradiction when the diff supports the stated behavior.

I retained this condition when revising the silent drift check because the initial evaluation exposed an overly strict interpretation of illustrative output differences. The revision allows the rubric to evaluate the actual behavior supported by the diff without overlooking genuine contradictions, missing requirements, or unexplained scope changes.

**Trade-offs**

The revised silent drift check is less likely to reject a PR solely because an illustrative output string differs from an example. This improves agreement on cases such as pkg-16, but it requires the evaluator to distinguish harmless presentation differences from material behavioral contradictions. I reran pkg-03, pkg-04, and pkg-16 as canaries and obtained 3/3 agreement; I also reran pkg-08 and pkg-19 and obtained 2/2 agreement. The final full evaluation achieved 20/20 agreement.

**Live precheck result**

Verdict: reject

The live precheck rejected PR #78 because the commit message does not follow the repository’s required <type>(<scope>): <description> format. The existing commit message is Fix async mocks in review service tests. I left the existing PR and its commit history unchanged rather than amending and force-pushing during this planning and precheck exercise. The evaluation harness result was separate: the final full evaluation achieved 20/20 agreement, passing the required 18/20 threshold.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
