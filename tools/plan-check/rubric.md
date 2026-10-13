# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis & Grounding | The candidate plan's diagnosis, read against the Issue and Repro evidence blocks in eval mode, or the student's posted reproduction evidence and issue thread in live mode; use the Diagnosis and grounding section of `references/evidence-guide.md`. | The stated cause or working diagnosis is consistent with the reproduced behavior and provides a plausible explanation for the observed behavior. If the internal cause is not directly established by the available evidence, the plan may treat it as a working hypothesis when the proposed change is bounded and the test plan provides a way to validate the reported behavior. The plan must not contradict the reproduction evidence or present a clearly unsupported explanation as established fact. | required |
| Bounded Scope | The candidate plan's Scope statement, including in-scope, not-in-scope, and named files or areas; use the Scope section of `references/evidence-guide.md`. | The proposed change is limited to the diagnosed problem and identifies meaningful unrelated work that is out of scope. The plan does not leave the implementation open-ended or silently include unrelated cleanup or behavior changes. | required |
| Executability | The candidate plan's named files or areas, approach, and change steps; use the Executability section of `references/evidence-guide.md`. | A developer who did not author the plan could begin the work from the stated files or areas and approach without needing the author to supply a missing essential decision about what to investigate or change. | required |
| Honesty & Unknowns | The candidate plan's diagnosis, scope, approach, test plan, risks, unknowns, and any deviation note, checked against the Issue and Repro evidence; use the Honesty section of `references/evidence-guide.md`. | The plan does not contradict known evidence or present a materially unsupported claim as established fact. Confirmed observations, working hypotheses, and unresolved implementation details are distinguished when that distinction affects the proposed work. A plan does not need to list an unknown separately when the available evidence is sufficient for the proposed bounded plan and test, and it may state a reasonable implementation hypothesis without treating it as proven. | required |
| Observable Test | The candidate plan's Test plan, read against the reproduction steps, expected and actual behavior, controls, and other artifacts in the Repro evidence; use the Test plan section of `references/evidence-guide.md`. | The test plan defines an observable result that can demonstrate whether the proposed change fixes the reported behavior and tests the relevant reproduction path or an equivalent real-path behavior. | required |
| Thread & Repo Communication | The candidate plan comment, read against the Issue, Thread highlights, Repo facts, and candidate plan; use the Comms section of `references/evidence-guide.md`. | The comment accurately represents the plan, available evidence, and implementation status. It distinguishes proposed work from work already completed and verified. If implementation is already complete, the comment explicitly identifies itself as retrospective and reports results supported by the plan or verification evidence. It follows applicable repository communication, contribution, and AI-use requirements. If the thread contains no relevant maintainer or contributor request, no response to such a request is required. | required |

## Verdict rule

Return `accept` only when every required check passes.

If any required check is `fail` or `unclear`, return `reject`.

All six checks are required, so no check is advisory and there are no preferred checks that can be ignored for the verdict.

The final verdict must be binary: `accept` or `reject`.
