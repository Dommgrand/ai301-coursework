# Evidence guide: where proof lives in a reproduction package
## Environment

Where it lives:
- Eval mode: the issue's Environment/details in the package and the candidate repro report's Environment section.
- Live mode: the issue page and the candidate's repro report.
- Also check the repo-facts block for required bug-report fields when applicable.

What good looks like:
- The candidate records the versions, operating system, and other environment details relevant to the issue's target.
- If the candidate tests in a different environment from the reporter, the difference is stated rather than presented as an exact match.

## Steps

Where it lives:
- Eval mode: the issue's stated reproduction steps and the candidate repro report's Preparation/Steps/Execution sections.
- Live mode: the issue's reproduction instructions and the candidate's repro report.

What good looks like:
- A stranger can identify the starting state and follow the candidate's actions through the trigger without guessing a missing setup or action.
- The candidate's steps preserve the inputs and conditions that matter to the issue.

## Behavior shown

Where it lives:
- Eval mode: the issue's reported/expected behavior and the candidate repro report's commands, output excerpts, logs, screenshots, or other artifacts.
- Live mode: the issue and the candidate's posted or referenced reproduction evidence.

What good looks like:
- The evidence either shows the failure condition described by the issue or provides a concrete reproduction attempt with an observable result that is honestly reported as not reproducing the issue.
- When the issue is not reproduced, the candidate identifies the relevant differences or limitations; a different or adjacent error must not be presented as the reported bug.

## Honesty

Where it lives:
- Eval mode: the candidate claim comment and repro report, checked against the issue context and the evidence shown in the report.
- Live mode: the candidate's draft comments, checked against the issue and the reproduction evidence.

What good looks like:
- Conclusions match what the evidence actually establishes, including an honest statement when the issue cannot be reproduced.
- The candidate does not present unsupported causes, frequency claims, universality claims, or priority judgments as established facts.

## Comms

Where it lives:
- Eval mode: the candidate claim comment and repro report, compared with the repo-facts bug-report template, contribution policy, and stated AI policy.
- Live mode: the candidate's draft comments and the repository's issue/contribution/AI-use guidance.

What good looks like:
- Required repository fields, disclosures, and contribution conventions are followed when they apply.
- The claim and report are specific to the issue and make only factual, supportable statements rather than boilerplate assurances.
