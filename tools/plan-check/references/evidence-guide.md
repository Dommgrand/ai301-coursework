# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

Where it lives:
- Eval mode: the candidate plan's Diagnosis section, read against the Repro evidence block and the Issue section.
- Live mode: the candidate plan's diagnosis, read against the student's posted reproduction comment and the issue thread.
- If the plan relies on a thread statement or maintainer finding, also check the Thread highlights in eval mode or the corresponding issue-thread comment in live mode.

What good looks like:
- The stated cause or working diagnosis is consistent with the observed behavior shown by the reproduction evidence.
- A plan may use a plausible working diagnosis even when the internal implementation cause has not yet been directly proven, provided the plan does not contradict the evidence and its bounded change and test plan can validate the reported behavior.
- Confirmed observations and hypotheses are distinguished when the distinction matters to the proposed work.

## Scope

Where it lives:
- Eval mode: the candidate plan's Scope section, including its in-scope and not-in-scope statements, plus the named files or areas in the plan.
- Live mode: the candidate plan's scope statement and named files or areas, checked against the issue and reproduction evidence.
- Use the Repo facts block when repository constraints or contribution expectations affect what may reasonably be changed.

What good looks like:
- The proposed change addresses the diagnosed problem through a defined and limited set of files, areas, or behaviors.
- The plan identifies meaningful work that is out of scope so a drive-by rewrite or unrelated fix is not silently included.

## Executability

Where it lives:
- Eval mode: the candidate plan's files/areas, approach, and change steps.
- Live mode: the candidate plan's files/areas and approach, checked against the issue and reproduction evidence for the target behavior.

What good looks like:
- A stranger can identify where to begin and what change to investigate or make without needing the author to supply a missing essential decision.
- The approach provides enough concrete direction to begin implementation while leaving room for normal implementation details discovered during the work.

## Test plan

Where it lives:
- Eval mode: the candidate plan's Test plan section, read against the Repro evidence block's reproduction steps, expected behavior, actual behavior, controls, and other observable artifacts.
- Live mode: the candidate plan's Test plan, read against the student's posted reproduction evidence and the issue's expected behavior.
- Use the Repo facts block when repository-specific test commands or conventions are relevant.

What good looks like:
- The test plan names an observable result that would demonstrate whether the proposed change fixes the reported behavior.
- The test covers the relevant reproduction path or an equivalent real-path check and distinguishes success from failure rather than merely stating that tests should pass.

## Honesty

Where it lives:
- Eval mode: the candidate plan's Diagnosis, Scope, Approach, Test plan, Risks, and Unknowns statements, checked against the Issue and Repro evidence blocks.
- Live mode: the candidate plan and draft plan comment, checked against the issue, reproduction evidence, and any documented deviations.
- If a deviation has been recorded, read the updated plan's deviation note as part of the evidence.

What good looks like:
- Confirmed observations, working hypotheses, risks, and unresolved implementation details are distinguished when the distinction affects the proposed work.
- A reasonable implementation hypothesis may be used when it is consistent with the evidence and the plan provides a bounded way to validate the reported behavior.
- The plan does not present a materially unsupported claim as established fact or contradict the reproduction evidence.
- An explicit unknown is useful when the missing information could materially change the scope, approach, or expected result; not every plan requires a separate unknown statement.

## Comms

Where it lives:
- Eval mode: the candidate plan comment, read against the Thread highlights, Issue, Repo facts, and the candidate plan.
- Live mode: the draft plan comment, read against the live issue thread, the candidate plan, and repository contribution guidance.
- Check the Repo facts block for stated contribution policies, required disclosures, templates, and AI-use rules.

What good looks like:
- The comment accurately summarizes the plan and evidence without making stronger claims than the package supports.
- The comment responds to relevant maintainer or contributor signals and follows applicable repository communication and AI-use requirements.
