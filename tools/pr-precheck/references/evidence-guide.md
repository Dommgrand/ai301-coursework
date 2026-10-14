# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

**Where it lives**

- **Eval mode:** Read the plan-context block for the issue, scope boundary, expected behavior, test plan, and documented deviations. Compare those with the candidate PR's changed-file list, commits, unified diff, title, and description.
- **Live mode:** Read `plan.md` and its deviation notes. Compare them with `git diff <default-branch>...HEAD`, the commit list, the issue description and relevant maintainer discussion, and `pr_draft.md`.

**What good looks like**

Every changed file and material behavior is within the plan's stated boundary or is explained by a documented deviation. The title and description accurately describe the change shown in the diff and do not claim behavior or completeness that the evidence fails to support. Silent expansion, unexplained omissions, and contradictory claims are evidence of silent drift.

## Test evidence (harness category: not-tested)

**Where it lives**

- **Eval mode:** Read the package's test-evidence section and compare its commands and observed outcomes with the plan-context block's test plan and the repo-facts block's required checks.
- **Live mode:** Read `test_evidence.md`, the plan's test plan and assigned reproduction steps, and the repository's documented test instructions or required checks. Inspect actual command output when it is included or available.

**What good looks like**

The evidence identifies what was run and what happened, with observable before-and-after behavior for the relevant reproduction when applicable. Results support the claims made in the description, and missing checks, failures, or environment limitations are disclosed rather than presented as successes. A disclosed shortfall is not automatically disqualifying; determine whether the remaining evidence and the repository's stated requirements permit submission.

A bare statement such as "tests pass" is weak when it does not identify the relevant test or observable result. Source code or an assertion in the plan does not prove a test was executed.

## Diff quality (harness category: unreviewable)

**Where it lives**

- **Eval mode:** Inspect the candidate PR's unified diff, changed-file list, and commit list.
- **Live mode:** Inspect the current branch's diff against the repository's default branch and the commit list. Compare the changed files with the plan's stated boundary.

**What good looks like**

The intended fix is identifiable in the diff, and the changes are relevant to the plan or supported by a documented dependency. Unrelated edits, generated artifacts, debug output, abandoned code, commented-out blocks, accidental files, or formatting churn are concerns when they materially obscure the change or make it harder to assess.

Do not treat the number of files, length of the diff, or commit count as proof of poor quality. Judge the actual content and whether the change remains reviewable.

## Standards and comms (harness category: standards-wall)

**Where it lives**

- **Eval mode:** Read the repo-facts block for required PR-template sections, contribution instructions, applicable policies, and AI-use disclosure rules. Compare these with the candidate PR title and description and any relevant issue-thread or maintainer direction included in the bundle.
- **Live mode:** Inspect the repository's `.github/PULL_REQUEST_TEMPLATE.md` (or the actual template location used by the repository), `CONTRIBUTING.md` when present, stated contribution and AI-use policies, and relevant maintainer direction in the issue thread. Compare those requirements with `pr_draft.md` and any required checklist or disclosure fields.

**What good looks like**

Every applicable required template section and disclosure is completed truthfully, and relevant maintainer instructions are addressed. Boilerplate, empty required fields, misleading statements, and omitted mandatory disclosures indicate a standards problem. Only enforce requirements supported by the available repository evidence; do not invent policies or assume a field is mandatory without evidence.

Whether the description accurately represents the implementation belongs to plan fidelity. This category concerns compliance with the repository's stated communication, template, and disclosure requirements.
