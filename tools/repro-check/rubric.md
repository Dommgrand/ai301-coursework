# Rubric: is this reproduction package ready to post?

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment | Candidate repro report's Environment section; compare with the issue's stated environment and the repo-facts bug-report requirements in the package. | The report records the relevant version, operating system, and other required environment details, and explicitly identifies meaningful differences from the issue's reported environment. | required |
| Steps | Candidate repro report's Preparation, Steps, and Execution sections; compare with the issue's stated reproduction steps. | A stranger can follow the candidate's setup and actions from the stated starting state through the issue's trigger without guessing a required step, input, or condition. | required |
| Behavior Match | Candidate repro report's commands, outputs, logs, screenshots, or other artifacts; compare the observed result with the issue's reported behavior and expected result. | The evidence either demonstrates the same failure condition described by the issue, or honestly documents a concrete reproduction attempt that did not reproduce the issue and clearly states the relevant differences or limitations. Evidence of a different or adjacent error must not be presented as reproduction of the issue. | required |
| Outcome Honesty | Candidate claim comment and repro report, checked against the issue context and the evidence shown in the report. | The candidate's conclusions do not exceed what the evidence establishes. Unsupported causes, frequency claims, universality claims, or priority judgments are not presented as facts. An honest cannot-reproduce result is acceptable when stated accurately. | required |
| Repo Communication | Candidate claim comment and repro report; compare with the package's bug-report template, contribution policy, and stated AI-use policy. | The candidate follows applicable repository conventions and required disclosures, and communicates a specific, factual claim without unsupported assurances or boilerplate replacing evidence. | required |

## Verdict rule

Return `accept` only when every required check passes.

If any required check is `fail` or `unclear`, return `reject`.

Preferred checks, if added later, never change the verdict.

In claim-only live mode, exclude checks whose required evidence is the repro report from the verdict, as directed by `SKILL.md`. Grade those checks as `unclear` with evidence `not yet applicable: claim-only draft`.
