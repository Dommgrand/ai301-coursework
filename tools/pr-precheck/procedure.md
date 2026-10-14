# Procedure: how this tool grades a PR package

## Read order

1. Identify the grading mode. In eval mode, use only the self-contained package supplied by the harness. In live mode, read `scope.md` first and stop if the repository is outside the allowed scope or the required scope value is still a placeholder.
2. Read the plan and record its issue, stated problem, intended behavior, in-scope files or components, expected behavior, test plan, and documented deviations. If the assignment supplies a specific reproduction pack, record which reproduction steps apply.
3. Read the issue context and repository facts. Record the issue's requirements and relevant maintainer direction, the repository's required checks, contribution rules, PR-template asks, and applicable AI-use disclosure policy. In eval mode, use only the corresponding bundle sections.
4. Read the commit list and unified diff. Record changed files, the behavior changed, any unrelated edits or leftover material, and whether the implementation matches the plan. Do not infer that a test passed from the code or a description.
5. Read the test evidence. Record the commands actually run, observed outputs, before-and-after reproduction results, repository checks, failures, and explicitly disclosed limitations. Compare the results with the plan's test plan and required repository checks.
6. Read the draft PR title and description. Compare every material claim with the diff and observed test evidence. Check required template fields and disclosures against the repository facts.
7. In live mode, read `voice-guide.md` and identify specific title or description violations. Report them with evidence and suggest accurate corrections. The voice guide does not independently determine the verdict unless a corresponding requirement is in the rubric.
8. Once these materials are gathered, grade each rubric check in the order it appears. This order establishes the plan and requirements before the proposed change and its claims are evaluated.

## Evidence gathering

### Plan fidelity / silent drift
- List the files and behaviors the plan says will change, the expected result, and any documented deviations.
- Compare that list with the changed-file list and unified diff. Identify changes outside the plan, planned behavior not implemented, and any material differences that need explanation.
- Compare the PR title and description with the actual diff and issue requirements. Record claims that the diff supports, contradicts, or cannot establish.
- Treat a deviation as disclosed only when the plan or description clearly identifies what differs and accurately explains its status. Do not assume that a vague statement covers a specific discrepancy.

### Test evidence / not tested
- Extract each test or reproduction command and its actual result from the evidence section.
- Compare the commands with the plan's test plan, relevant issue reproduction steps, and the repository's stated required checks.
- Record before-and-after results when available. Distinguish a test that was run and failed from a test that was never run.
- Identify claims such as "fixed," "passes," or "reproduced" and verify that the recorded results support them.
- Record any missing validation, known failure, environment limitation, or other shortfall and whether it is explicitly disclosed. Do not manufacture test results or treat source code alone as proof of execution.

### Diff quality / unreviewable
- Review the changed-file list and unified diff against the plan's boundary.
- Identify unrelated files or hunks, generated artifacts, debug leftovers, dead or commented-out code, accidental files, and formatting-only churn.
- Decide whether those items materially obscure the intended change or make it difficult to evaluate. Record the specific file or hunk that supports the decision.
- Do not fail a change merely because it is long or touches multiple files; use the plan and evidence to decide whether the extra material is justified.

### Standards and comms / standards wall
- Extract the repository's actual PR-template fields, contribution requirements, relevant maintainer instructions, and applicable AI-use disclosure requirements from the available repository facts.
- Compare each applicable requirement with the draft PR title and description and any required checklist or disclosure fields included in the package.
- Record each missing, misleading, or contradicted requirement. Do not invent policies or assume a disclosure is required unless the evidence supports that conclusion.
- In live mode, also apply the voice guide to the title and description, report specific violations, and suggest corrections without changing the factual meaning.

## Check execution

1. Apply the four rubric checks in table order: `silent drift`, `not tested`, `unreviewable`, and `standards wall`.
2. For each check, use the evidence already gathered for its named evidence family. Re-read a source only when a recorded fact is incomplete or a specific claim needs verification.
3. Grade the check `pass` only when its stated pass condition is supported. Grade it `fail` when evidence demonstrates that the condition is not met. Grade it `unclear` when the available evidence cannot establish either outcome.
4. If required evidence is absent, do not infer success. Apply the rubric's pass condition to decide whether the absence itself is a failure or leaves the check unclear. An unverifiable required condition cannot support acceptance.
5. Apply the honest-outcome rule. A clearly disclosed limitation or deviation is not automatically a failure. Decide whether it is compatible with the repository's stated submission requirements and the check's pass condition. Disclosure does not excuse a requirement that must be satisfied before submission.
6. Keep evidence specific and concise. Record the relevant file, test command and result, issue requirement, template field, or short decisive quote. Do not use general impressions as evidence.
7. Do not add new rubric checks or change pass conditions during grading. If a procedural gap prevents a check from being completed, identify the gap and grade according to the rubric's stated treatment of missing or unverifiable evidence.

## Verdict assembly

1. Apply the rubric's verdict rule after all four checks have grades.
2. Return `accept` only if every required check is `pass`. Return `reject` if any required check is `fail` or `unclear`. Preferred checks, if present, do not change the verdict.
3. If more than one required check fails or is unclear, identify the first such check in rubric table order as the deciding check. Include its decisive evidence in that check's evidence field and make the reason for rejection clear in the readable summary.
4. Include every rubric check in the final JSON output, preserving the rubric check names and using only `pass`, `fail`, or `unclear` as grades.
5. Use the PR URL as `item` in live mode when available; otherwise use the package or bundle identifier supplied by the harness.
6. End the completed grading response with one fenced JSON block matching the schema in `SKILL.md`. The JSON verdict must match the rubric rule, and no text may follow the final JSON block.
