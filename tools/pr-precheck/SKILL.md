---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading



## The question

Answer exactly one question: Is this PR package ready to submit?

A package includes the plan and documented deviations, proposed changes, test evidence, and draft PR title and description. Judge it against the issue it intends to resolve and applicable repository requirements. Do not grade the contributor or treat polished writing as proof that the implementation is correct.

## Inputs and modes

Determine the mode before grading.

**Live mode:** Read `plan.md` and its deviation notes, the current branch's full diff against the repository's default branch (`git diff main...HEAD` if `main` is the default branch), `pr_draft.md`, `test_evidence.md`, the target issue and relevant discussion, repository contribution instructions, the PR template, applicable policies, `scope.md`, and `voice-guide.md`. Run Git commands from the repository working copy. For house-chain students, use the specified house reproduction pack instead of ordinary Unit 6 reproduction steps where applicable. Never claim a test or reproduction was run unless evidence shows it.

**Eval mode:** Treat the supplied bundle as the entire world. Use only its plan, issue context, repository facts, diff, test evidence, title, and description. Do not fetch outside information or inspect a working copy. Grade every required check and apply the full verdict rule. Do not silently switch modes.

## The scope seam (live mode only)

Read `scope.md` before inspecting the issue or grading any artifact. Confirm that the target repository matches its `Repo:` value. If the repository is outside scope, refuse to grade it. If the `Repo:` value is empty or remains a placeholder, stop and tell the user to enter their cohort's exact Path Review repository; do not guess. In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

Read `voice-guide.md` in live mode and check the draft PR title and description against its communication rules. Report concrete violations and suggest evidence-based corrections. The guide does not independently determine the verdict; it matters to a required check only when the rubric makes the issue material, such as a misleading or unsupported claim. In eval mode, ignore `voice-guide.md` entirely.

## Component reads

`rubric.md` defines the checks, pass conditions, and verdict rule. `procedure.md` defines the review steps and must be followed as written. `references/evidence-guide.md` maps evidence categories to their sources. Use `scope.md` and `voice-guide.md` only as described for live mode.

If `rubric.md` or `procedure.md` lacks substantive content, refuse to grade and identify the missing component. Headings or comments alone do not count as substantive content. If the procedure is silent on a step, report the gap rather than improvising or claiming it was completed. If evidence cannot establish a check's result, mark it `unclear`.

## Verdict and output

Use only two verdicts: `accept` means every required check passes and the package is ready to submit; `reject` means at least one required check fails or remains unclear under the rubric's rule. Run every required check. Give each check a `pass`, `fail`, or `unclear` grade and one concise evidence line naming the fact or quote that decided it.

End the response with the valid fenced JSON block below, including every required check. It must be the final content, with nothing after it. Preserve the schema exactly.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- **Evidence first:** Gather and cite observable evidence before assigning grades. Distinguish claims in the plan or PR description from facts demonstrated by the diff, test output, issue, and repository standards.
- **Grade the change, not the polish:** Judge whether the proposed change fulfills its stated scope and is supported by evidence. Do not reward polished wording when the implementation or tests contradict it.
- **The rubric decides what passes:** Apply the written pass conditions and verdict rule consistently. Do not invent checks, silently change requirements, or excuse a failure because the overall change looks good.
- **The procedure decides how to grade:** Follow the evidence-gathering and grading steps in `procedure.md`. If a required step or input is missing, report the gap instead of pretending it was completed.
- **Handle unclear evidence consistently:** Grade each check `pass`, `fail`, or `unclear` based on the evidence. If the rubric does not say how an unclear check affects the verdict, treat it as a failure for verdict purposes and explain why.
- **Distinguish honest limitations from silent drift:** A clearly documented limitation or deviation is not automatically a rejection. Apply the rubric's actual conditions and check whether the description accurately discloses the shortfall.
- **Keep the decision auditable:** Each check must include a concise evidence line identifying the fact or quote that determined its grade. The final verdict must follow the rubric's verdict rule.
